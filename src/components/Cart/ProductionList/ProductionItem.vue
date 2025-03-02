<template lang="">
    <div>
       product: {{item.product}} price :  {{item.price}} <button @click="clickHandler(item.id, $event)"> add to </button>
    </div>
</template>
<script>
import event from '../event';

export default {
    props: {
        item: {
            default() {
                return {
                    id: 1,
                    product: 'a'
                }
            }
        }
    },
    methods: {
        clickHandler(id, e) {
            e.preventDefault();
            event.$emit('addToCart', id)
        }
    }
}
</script>
<style lang="">

</style>