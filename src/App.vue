<script setup>
import { reactive } from 'vue';

const estado = reactive({
  valor1: 0,
  valor2: 0,
  resultado: 0
})


function calcula() {
  var num1 = Number(estado.valor1)
  var num2 = Number(estado.valor2)
  var operacao = document.getElementById('operacao').value
  var mostrador = document.getElementById('resultado')
  var aguarde = document.getElementById('aguarde')
  var parabens = document.getElementById('title-parabens')

  if(operacao === '+') {
    estado.resultado = num1 + num2
  } else if (operacao === '-') {
    estado.resultado = num1 - num2
  }

  aguarde.innerHTML = ''
  parabens.innerHTML = 'PRBNS!'
  mostrador.innerHTML = `Voilá! O resultado é incríveis ${estado.resultado}`
}



</script>

<template>
  <div class="body">
    <header>
      <h1 id="title-parabens">CAL <br> CULA <br> DORA </h1>
      <div class="calculadora">
        <p>insert a número</p>
        <input :class="{ bordergreen: estado.valor1 > 0 }" @keyup="evento => estado.valor1 = evento.target.value" style="border:1px solid black; padding: 0.5rem; width: 300px;" type="number" id="input1">
        <p>Choose your operação</p>
        <select style="border:1px solid black; padding: 0.5rem; width: 45px;" id="operacao">
          <option value="+">+</option>
          <option value="-">-</option>
        </select>
        <p>insira outro number</p>
        <input :class="{ bordergreen: estado.valor2 > 0 }" @keyup="evento => estado.valor2 = evento.target.value" style="border:1px solid black; padding: 0.5rem; width: 300px; padding-bottom: 5px;" type="number" id="input2">
        <button style="padding: 0.7rem; width: 300px;"  @click="calcula()">Calculate</button>
      </div>
    </header>
    <div style="margin-left: 20rem; margin-top: 5rem;" class="valor-resultado">
      <p style="padding-bottom: 0.4rem;" id="aguarde">Prepare-se para o show</p>
      <p style="font-size: 1rem; padding-left: 10rem; padding: 5rem; border: 1px solid white; " id="resultado">Aguarde a Mágica...</p>
    </div>
  </div>
</template>

<style scoped>

.bordergreen {
  background-color: rgb(219, 255, 219);
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: greyscale;
  font-family: sans-serif;
}

.body {
  display: flex;
  background-color: #121214;
  color: white;
  padding: 12rem 13.4rem 14rem 11rem;
  margin: 0;
}

header {
  max-width: 30rem;
}

header h1 {
  font-size: 4.8rem;
  font-weight: 400;
  line-height: 5rem;
  padding-bottom: 1.8rem;
}

.calculadora {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.valor-resultado {
  margin-left: 30px;
}

.valor-resultado h1 {
  font-size: 20rem;
}

.container {
  max-width: 1600px;
  margin: 0 auto;
  padding-top: 4rem;
  padding-bottom: 500px;
}

</style>
