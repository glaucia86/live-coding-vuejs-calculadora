<template>
  <div class="calculadora">
    <div class="display">0</div>
    <div class="botao">C</div>
    <div class="botao">+/-</div>
    <div class="botao">%</div>
    <div class="botao operadores">÷</div>
    <div class="botao">7</div>
    <div class="botao">8</div>
    <div class="botao">9</div>
    <div class="botao operadores">x</div>
    <div class="botao">4</div>
    <div class="botao">5</div>
    <div class="botao">6</div>
    <div class="botao operadores">-</div>
    <div class="botao">1</div>
    <div class="botao">2</div>
    <div class="botao">3</div>
    <div class="botao operadores">+</div>
    <div class="botao zero">0</div>
    <div class="botao">.</div>
    <div class="botao operadores">=</div>
  </div>
</template>

<script>
export default {

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.calculadora {
  margin: 0 auto;
  width: 350px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: 1 / 5;
  background-color: #333;
  color: white;
}

.zero {
  grid-column: 1 / 3;
}

.botao {
  background-color: #f2f2f2;
  border: 1px solid #999;
}

.operadores {
  background-color: orange;
  color: white;
}
</style>
