<script setup>
    const model = defineModel()
    defineEmits(['inputEvent'])

</script>
<template>
    <input type="text" v-model="model" @keyup.enter="$emit('inputEvent')" placeholder="Digite a tarefa aqui">
</template>
<style scoped>
input {
    min-height: 46px;
    padding: 0 14px;
    border: 1px solid transparent;
    border-radius: 9px;
    outline: none;
    background: #f3f6f3;
    color: #20392d;
    font: inherit;
    font-size: 15px;
    transition: border-color 160ms ease, background-color 160ms ease, box-shadow 160ms ease;
}

input::placeholder {
    color: #829087;
}

input:focus {
    border-color: #91aa98;
    background: #fff;
    box-shadow: 0 0 0 3px rgba(72, 112, 83, 0.12);
}

@media (prefers-reduced-motion: reduce) {
    input {
        transition: none;
    }
}
</style>