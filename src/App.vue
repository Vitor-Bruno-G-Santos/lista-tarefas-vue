<script setup>
import Text from '@/components/input/Text.vue'
import Button from '@/components/input/Button.vue';
import List from '@/components/list/List.vue';
import { ref } from 'vue';

const textoTemp = ref('')
const tarefas = ref([])
let proximoId = 1

function send(){
    const texto =  textoTemp.value.trim()
    if (!texto) return

    tarefas.value.push({id: proximoId++, texto, done: false})
    textoTemp.value = ''
}
function remover(id){
    tarefas.value = tarefas.value.filter(t => t.id !== id)
}

function alternar(id, valor){
    const tarefa = tarefas.value.find(t => t.id === id)
    if (tarefa) tarefa.done = valor
}

</script>
<template>
    <div class="inputWrapper">
        <Text v-model="textoTemp" @inputEvent="send"></Text>
        <Button @func='send' name="Adicionar"></Button>
    </div>
    <div></div>
    <List :infos=tarefas @remove="remover" @toggle="alternar"></List>
</template>
<style scoped>
:global(*) {
    box-sizing: border-box;
}

:global(body) {
    min-width: 320px;
    min-height: 100vh;
    margin: 0;
    background-color: #f3f6f3;
    background-image: radial-gradient(circle, rgba(32, 57, 45, 0.08) 1px, transparent 1px);
    background-size: 24px 24px;
    color: #20392d;
    font-family: "Avenir Next", Avenir, "Segoe UI", sans-serif;
    -webkit-font-smoothing: antialiased;
}

:global(#app) {
    width: min(100% - 40px, 760px);
    margin: 0 auto;
    padding: 11vh 0 72px;
}

.inputWrapper {
    display: flex;
    width: min(100%, 680px);
    gap: 10px;
    align-items: stretch;
    margin: 0 auto 24px;
    padding: 8px;
    border: 1px solid #dce5de;
    border-radius: 15px;
    background: #fff;
    box-shadow: 0 12px 32px rgba(32, 57, 45, 0.08);
}

.inputWrapper > input {
    flex: 1;
    min-width: 0;
}

.inputWrapper > button {
    flex: 0 0 auto;
}

@media (max-width: 480px) {
    :global(#app) {
        width: min(100% - 28px, 760px);
        padding-top: 8vh;
    }

    .inputWrapper {
        gap: 7px;
        padding: 6px;
    }
}
</style>