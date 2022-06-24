<template>
    <button v-on:click="onClick()" v-bind:style="{background: color}" class="btn">{{text}}</button>
</template>


<script>
export default {
    name: 'Button-app',
    props: {
        text: String,
        color: String
    },
    methods: {
        onClick() {
            this.$emit('btnClick')
        }
    }
}
</script>

<style scoped>
</style>