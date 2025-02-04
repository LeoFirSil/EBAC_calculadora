<script setup>
import { reactive, computed } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: 'soma'
});

const resultado = computed(() => {
  switch (estado.operacao) {
    case 'soma':
      return estado.num1 + estado.num2;
    case 'subtração':
      return estado.num1 - estado.num2;
    case 'multiplicação':
      return estado.num1 * estado.num2;
    case 'divisão':
      return estado.num2 !== 0 ? estado.num1 / estado.num2 : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});

const atualizarValor1 = (novoValor) => {
  estado.num1 = novoValor;
};

const atualizarValor2 = (novoValor) => {
  estado.num2 = novoValor;
};

const atualizarOperacao = (novaOperacao) => {
  estado.operacao = novaOperacao;
};
</script>

<template>
  <div class="container">
    <Cabecalho />
    <Formulario :insValor1="estado.num1" :insValor2="estado.num2" :operadores="estado.operacao" :result="resultado"
      @update:valor1="atualizarValor1" @update:valor2="atualizarValor2" @update:operacao="atualizarOperacao" />
  </div>
</template>

<style scoped>
.container {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  max-width: 600px;
  height: 300px;
  background-color: blueviolet;
  border-radius: 8px;
  border: 5px dotted #000;
}
</style>