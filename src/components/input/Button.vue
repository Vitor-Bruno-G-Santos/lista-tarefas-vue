<script setup>
defineProps(['func', 'name'])
</script>
<template>
    <button @click='$emit("func")'>{{ name }}</button>
</template>
<style scoped>
button {
    min-height: 46px;
    padding: 0 18px;
    border: 1px solid #20392d;
    border-radius: 10px;
    background: #20392d;
    color: #fff;
    font: inherit;
    font-size: 14px;
    font-weight: 650;
    cursor: pointer;
    transition: background-color 160ms ease, border-color 160ms ease, transform 160ms ease;
}

button:hover {
    border-color: #b95536;
    background: #b95536;
}

button:active {
    transform: translateY(1px);
}

button:focus-visible {
    outline: 3px solid rgba(185, 85, 54, 0.35);
    outline-offset: 3px;
}

@media (prefers-reduced-motion: reduce) {
    button {
        transition: none;
    }
}
</style>