<template lang="">
    <div >
        <div v-for="item in list" :key="item.id">
            <!-- {{item}} -->
            product: {{item.product}}
            price: {{item.price}}
            quantity: {{item.quantity }}
        </div>
        <h2>total11: {{totalPrice}}</h2>
    </div>
</template>
<script>
export default {
    props: {
        productionList: {
            default() {
                return []
            }
        },
        cartList: {
            default() {
                return []
            }
        }
    },
    computed: {
        list() {
            return this.cartList.map(cartListItem => {
                const productionItem = this.productionList.find(
                    prdItem => prdItem.id === cartListItem.id
                )

                return {
                    ...productionItem,
                    quantity: cartListItem.quantity
                }
            })
        },
        totalPrice() {
            return this.list.reduce((acc, item) => {
                return acc + item.price * item.quantity
            }, 0)

        }
    }
}
</script>
<style lang="">

</style>