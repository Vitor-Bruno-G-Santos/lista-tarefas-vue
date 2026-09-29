<script setup>
import Button from '../input/Button.vue';
import Checkbox from '@/components/input/Checkbox.vue';

const emit = defineEmits(['remove', 'toggle'])
const props = defineProps({ infos: { type: Array, default: () => [] } })

</script>
<template>
    <table>
        <thead>
            <tr>
                <th>Tarefas</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="info in infos" :key="info.id" v-if="infos.length != 0">
                <td>
                    <Checkbox :id="`tarefa-${info.id}`" :model-value="info.done" @update:model-value="emit('toggle', info.id, $event)"></Checkbox>
                    <p :class="{ done: info.done }">{{ info.texto }}</p>
                    <Button @func="emit('remove', info.id)" name="Remover"></Button>
                </td>
            </tr>
            <tr v-else>
                <td>Nenhuma tarefa ainda</td>
            </tr>
        </tbody>
    </table>
</template>
<style scoped>
table {
    width: min(100%, 680px);
    margin: 0 auto;
    overflow: hidden;
    border: 1px solid #dce5de;
    border-spacing: 0;
    border-radius: 15px;
    background: #fff;
    box-shadow: 0 12px 32px rgba(32, 57, 45, 0.07);
}

th {
    padding: 16px 20px;
    background: #e7eee8;
    color: #466050;
    font-size: 12px;
    font-weight: 700;
    text-align: left;
}

td {
    display: flex;
    min-height: 68px;
    align-items: center;
    gap: 14px;
    padding: 12px 18px;
    border-top: 1px solid #e8eee9;
}

td p {
    flex: 1;
    min-width: 0;
    margin: 0;
    color: #30463a;
    font-size: 15px;
    line-height: 1.5;
    overflow-wrap: anywhere;
}

p.done {
    color: #89958d;
    text-decoration: line-through;
}

td button {
    min-height: 36px;
    padding: 0 12px;
    border-color: #e8d5cd;
    background: #fff;
    color: #a74f34;
    font-size: 13px;
}

td button:hover {
    border-color: #b95536;
    background: #b95536;
    color: #fff;
}

@media (max-width: 480px) {
    th {
        padding: 14px 16px;
    }

    td {
        min-height: 62px;
        gap: 10px;
        padding: 10px 12px;
    }

    td button {
        padding: 0 9px;
    }
}
</style>