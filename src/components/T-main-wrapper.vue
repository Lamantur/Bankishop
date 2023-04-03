<template>
    <div class="T-main-wrapper">
        <H1>{{ title }}</H1>
        <T-catalog :msge="msge" />
        <T-cart />

    </div>
</template>
<script>
import TCatalog from './T-catalog.vue'
import TCart from './T-cart.vue'

export default {
    props: ['msge'],
    components: {
        TCatalog,
        TCart
    },

    name: 'T-main-wrapper',


    data() {
        return {
            title: 'Картины эпохи Возрождения'
        }
    },
    computed: {},
    methods: {},
    watch: {},

}
</script>
<style>
.T-main-wrapper {
    display: grid;
    max-width: 1136px;
    margin: 0 auto;
}
</style>