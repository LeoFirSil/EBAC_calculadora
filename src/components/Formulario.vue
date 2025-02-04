<script setup>
import { ref, computed, watch } from 'vue';

const props = defineProps(['insValor1', 'insValor2', 'operadores', 'result']);
const emit = defineEmits(['update:valor1', 'update:valor2', 'update:operacao']);

const valor1 = ref(Number(props.insValor1));
const valor2 = ref(Number(props.insValor2));
const operacao = ref(props.operadores);

const resultado = computed(() => props.result);

watch(valor1, (novoValor) => {
    emit('update:valor1', novoValor);
});

watch(valor2, (novoValor) => {
    emit('update:valor2', novoValor);
});

watch(operacao, (novaOperacao) => {
    emit('update:operacao', novaOperacao);
});
</script>

<template>
    <form>
        <div class="row">
            <div class="col-md-9 mt-1 mb-3">
                <input v-model.number="valor1" type="number" />
                <input v-model.number="valor2" type="number" />
            </div>
            <div class="col-md-3">
                <select v-model="operacao">
                    <option value="soma">soma</option>
                    <option value="subtração">subtração</option>
                    <option value="multiplicação">multiplicação</option>
                    <option value="divisão">divisão</option>
                </select>
            </div>
        </div>
        <p>Resultado: {{ resultado }}</p>
    </form>
</template>

<style scoped>
p {
    margin-top: 10px;
    background-color: #fff;
    padding: 10px;
}
</style>