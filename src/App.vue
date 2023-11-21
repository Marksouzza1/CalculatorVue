<template>
  <div class="fundo">
    <div class="calculadora">
      <p id="resultado">{{ resultado }}</p>
      <button class="botao" @click="inserir('+')">+</button>
      <button class="botao" @click="inserir('-')">-</button>
      <button class="botao" @click="inserir('/')">/</button><br>
      <button class="botao" @click="inserir('7')">7</button>
      <button class="botao" @click="inserir('8')">8</button>
      <button class="botao" @click="inserir('9')">9</button><br>
      <button class="botao" @click="inserir('4')">4</button>
      <button class="botao" @click="inserir('5')">5</button>
      <button class="botao" @click="inserir('6')">6</button><br>
      <button class="botao" @click="inserir('1')">1</button>
      <button class="botao" @click="inserir('2')">2</button>
      <button class="botao" @click="inserir('3')">3</button><br>
      <button class="botao" @click="inserir('.')">.</button>
      <button class="botao" @click="inserir('0')">0</button>
      <button class="botao" @click="limpar()">C</button><br>
      <button class="botao" style="width: 156px;" @click="calcular()">=</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      resultado: '',
    };
  },
  methods: {
    inserir(num) {
      if (this.resultado === '' && (num === '.' || num === '/' || num === '*')) {
        return;
      }
      this.resultado += num;
    },
    limpar() {
      this.resultado = '';
    },
    calcular() {
      var input = this.resultado;
      var operador;
      if (input.indexOf('+') !== -1) {
        operador = '+';
      } else if (input.indexOf('-') !== -1) {
        operador = '-';
      } else if (input.indexOf('*') !== -1) {
        operador = '*';
      } else if (input.indexOf('/') !== -1) {
        operador = '/';
      }

      if (operador) {
        var partes = input.split(operador);
        var num1 = parseFloat(partes[0]);
        var num2 = parseFloat(partes[1]);

        switch (operador) {
          case '+':
            this.resultado = num1 + num2;
            break;
          case '-':
            this.resultado = num1 - num2;
            break;
          case '*':
            this.resultado = num1 * num2;
            break;
          case '/':
            if (num2 !== 0) {
              this.resultado = num1 / num2;
            } else {
              this.resultado = "Erro:";
            }
            break;
        }
      }
    },
  },
};
</script>

<style>

</style>
