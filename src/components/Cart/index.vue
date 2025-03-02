<template>
    <div>
        <ProductionList :list="productionList">{{ productionList }}</ProductionList>
        <hr>
         <CartList :productionList="productionList" :cartList="cartList"/>
    </div>
</template>

<script>
import ProductionList from './ProductionList/index'
import CartList from './CartList/index'
import event from './event'

export default {
    components: {
        ProductionList,
        CartList
    },
    data() {
        return {
            productionList: [
                { id: 'a1', product: 'pd1', price: 1 },
                { id: 'a2', product: 'p2', price: 2 },
                { id: 'a3', product: 'p3', price: 3 },
                { id: 'a4', product: 'p4', price: 4 },
            ],
            cartList: []
        }
    },
    methods: {
        addToCart(id) {
            const prod = this.cartList.find(item=> item.id === id)
            if(prod) {
                prod.quantity++
                return
            }
            this.cartList.push({id, quantity: 1})
        }
    },
    mounted() {
        event.$on('addToCart', this.addToCart)

    }
}
</script>