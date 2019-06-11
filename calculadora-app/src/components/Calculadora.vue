<template>
  <div class="calculadora">
    <div class="display">{{valorCorrente || '0'}}</div>
    <div v-on:click="limpar" class="botao">C</div>
    <div v-on:click="sinal" class="botao">+/-</div>
    <div v-on:click="porcentagem" class="botao">%</div>
    <div v-on:click="dividir" class="botao operadores">÷</div>
    <div v-on:click="juntarNumeros('7')" class="botao">7</div>
    <div v-on:click="juntarNumeros('8')" class="botao">8</div>
    <div v-on:click="juntarNumeros('9')" class="botao">9</div>
    <div v-on:click="multiplicar" class="botao operadores">x</div>
    <div v-on:click="juntarNumeros('4')" class="botao">4</div>
    <div v-on:click="juntarNumeros('5')" class="botao">5</div>
    <div v-on:click="juntarNumeros('6')" class="botao">6</div>
    <div v-on:click="diminuir" class="botao operadores">-</div>
    <div v-on:click="juntarNumeros('1')" class="botao">1</div>
    <div v-on:click="juntarNumeros('2')" class="botao">2</div>
    <div v-on:click="juntarNumeros('3')" class="botao">3</div>
    <div v-on:click="somar" class="botao operadores">+</div>
    <div v-on:click="juntarNumeros('0')" class="botao zero">0</div>
    <div v-on:click="ponto" class="botao">.</div>
    <div v-on:click="resultado" class="botao operadores">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      valorCorrente: '',
      numeroAnterior: null,
      operador: null,
      operadorClicado: false,
    };
  },
  methods: {
    /**
     * Método responsável por limpar o display da 'Calculadora':
     */
    limpar() {
      this.valorCorrente = '';
    },

    /**
     * Método responsável por colocar o sinal '-' ou '+' para a realização
     * de cálculos operacionais.
     * - chartAt --> https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/charAt
     * - slice --> https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
     */
    sinal() {
      this.valorCorrente = this.valorCorrente.charAt(0) === '-'
        ? this.valorCorrente.slice(1)
        : `-${this.valorCorrente}`;
    },

    // Método responsávelpor realizar operações de 'porcentagem'
    porcentagem() {
      this.valorCorrente = `${parseFloat(this.valorCorrente) / 100}`;
    },

    // Método responsável por juntar os números no display da Calculadora:
    juntarNumeros(numero) {
      if (this.operadorClicado) {
        this.valorCorrente = '';
        this.operadorClicado = false;
      }

      this.valorCorrente = `${this.valorCorrente}${numero}`;
    },

    // Método responsável por adicionar 'ponto' no display da Calculadora:
    ponto() {
      if (this.valorCorrente.indexOf('.') === -1) {
        this.juntarNumeros('.');
      }
    },

    setarValor() {
      this.numeroAnterior = this.valorCorrente;
      this.operadorClicado = true;
    },

    // Método responsável por realizar a operação da 'divisão'
    dividir() {
      this.operador = (num1, num2) => num1 / num2;
      this.setarValor();
    },

    // Método responsável por realizar a operação da 'multiplicar'
    multiplicar() {
      this.operador = (num1, num2) => num1 * num2;
      this.setarValor();
    },

    // Método responsável por realizar a operação da 'diminuir'
    diminuir() {
      this.operador = (num1, num2) => num1 - num2;
      this.setarValor();
    },

    // Método responsável por realizar a operação da 'somar'
    somar() {
      this.operador = (num1, num2) => num1 + num2;
      this.setarValor();
    },

    // Método responsável por apresentar o resultado das operações da Calculadora:
    resultado() {
      this.valorCorrente = `${this.operador(
        parseFloat(this.numeroAnterior),
        parseFloat(this.valorCorrente),
      )}`;
      this.numeroAnterior = null;
    },
  },
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
