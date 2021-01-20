<template>
    <li
    v-on:click="markAsDone"
    >O {{itemName}}</li>
</template>

<script>
export default {
    props: {
        itemData : Object,
        itemName : String
    },

    methods: {
        markAsDone() {
            this.$emit('marked', this.itemData)
        }
    }
}
</script>

<style>

</style>