<template>
  <div class="calculadora">
    <div class="display">0</div>
    <div>C</div>
    <div>+/-</div>
    <div>%</div>
    <div>÷</div>
    <div>7</div>
    <div>8</div>
    <div>9</div>
    <div>x</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
    <div>-</div>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>+</div>
    <div>0</div>
    <div>.</div>
    <div>=</div>
  </div>
</template>

<script>
export default {

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.calculadora {
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

</style>
