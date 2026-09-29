<script setup>
defineProps(['id'])
const model = defineModel({type:Boolean, default: false})
</script>
<template>
    <input type="checkbox" :id="id" v-model="model">
</template>
<style scoped>
input {
    width: 20px;
    height: 20px;
    flex: 0 0 20px;
    margin: 0;
    accent-color: #b95536;
    cursor: pointer;
}

input:focus-visible {
    outline: 3px solid rgba(185, 85, 54, 0.3);
    outline-offset: 3px;
}
</style>