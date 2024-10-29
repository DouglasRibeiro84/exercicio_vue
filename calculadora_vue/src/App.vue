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

<template class="body">
  <div class="container  p-5 b-black" data-bs-theme=dark>
    <header class="p-5 mb-4 mt-4 rounded-3 text-center">
      <h1 class="text-light">Calculadora Simples</h1>
      <form class="mt-4">
        <div class="caluladora d-flex justify-content-center">
          <div class="row">
            <div class="col-md-1"></div>
            <div class="col-md-3 mt-3 mt-sm-0">
              <input class="form-control text-center" type="number" v-model.number="estado.numero1">
            </div>
            <div class="col-md-4 mt-3 mt-sm-0 ">
              <select class="form-control text-center" v-model="estado.operacao">
                <option value="+">Somar ( + )</option>
                <option value="-">Subtrair ( - )</option>
                <option value="*">Multiplicar ( x )</option>
                <option value="/">Dividir ( / )</option>
              </select>
            </div>
            <div class="col-md-3">
              <input class="form-control mt-3 mt-sm-0 text-center " type="number" v-model.number="estado.numero2">
            </div>
            <div class="col-md-1"></div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-3 mt-5 "></div>
          <div class="col-md-6 mt-5 ">
            <span class="form-control fw-bold">Resultado: {{ resultado }} </span>
          </div>
          <div class="col-md-3 mt-5 "></div>
        </div>
      </form>
    </header>
  </div>
</template>

<style scoped>
header {
  border: 3px double black;
  background-color: rgba(128, 128, 128, 0.274);
}

h1 {
  text-shadow: 10px 10px 8px black;
}

.container {
  background-image: url(https://cdn.pixabay.com/photo/2020/10/27/08/00/mountains-5689938_640.png);
  background-size: cover;
  background-repeat: no-repeat;
  height: 100vh;
  max-width: 100%;
}

</style>
