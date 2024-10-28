<script setup>
import { computed, reactive } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: '+',
})

const resultado = computed(() => {
  switch (estado.operacao) {
    case '+':
      return estado.numero1 + estado.numero2;
    case '-':
      return estado.numero1 - estado.numero2;
    case '*':
      return estado.numero1 * estado.numero2;
    case '/':
      return estado.numero2 !== 0 ? estado.numero1 / estado.numero2 : 'Impossivel dividir por 0';
    default:
      return 0;
  }
})


</script>

<template>
  <div class="container mt-5 p-5">
    <header class="p-5 mb-4 mt-4 bg-secondary rounded-3 text-center">
      <h1 class="text-light">Calculadora</h1>
      <form class="mt-4">
        <div class="caluladora d-flex justify-content-center">
          <div class="row">
            <div class="col-md-4 mt-3 mt-sm-0">
              <input class="form-control" type="number" v-model.number="estado.numero1">
            </div>
            <div class="col-md-4 mt-3 mt-sm-0 ">
              <select class="form-control" v-model="estado.operacao">
                <option value="+">Somar ( + )</option>
                <option value="-">Subtrair ( - )</option>
                <option value="*">Multiplicar ( x )</option>
                <option value="/">Dividir ( / )</option>
              </select>
            </div>
            <div class="col-md-4">
              <input class="form-control mt-3 mt-sm-0 " type="number" v-model.number="estado.numero2">
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-12 mt-5 ">
            <span class="form-control fw-bold">Resultado:  {{ resultado }} </span>
          </div>
        </div>
      </form>
    </header>
  </div>
</template>

<style scoped>


</style>
