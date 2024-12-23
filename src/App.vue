<template>
  <div id="app">
    <div class="calculator">
      <h1>Calculadora Aritmética</h1>

      <!-- Campos de entrada -->
      <div class="inputs">
        <input 
          type="number" 
          v-model.number="numero1" 
          placeholder="Digite o primeiro número" 
        />
        <input 
          type="number" 
          v-model.number="numero2" 
          placeholder="Digite o segundo número" 
        />
      </div>

      <!-- Seleção da operação -->
      <div class="operation">
        <label for="operation">Escolha a operação:</label>
        <select v-model="operacao" id="operation">
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>

      <!-- Resultado -->
      <div class="result">
        <h2>Resultado: {{ resultado }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      numero1: 0, // Primeiro número
      numero2: 0, // Segundo número
      operacao: 'soma', // Operação selecionada (valor inicial: soma)
    };
  },
  computed: {
    // Propriedade computada que faz o cálculo automaticamente
    resultado() {
      switch (this.operacao) {
        case 'soma':
          return this.numero1 + this.numero2;
        case 'subtracao':
          return this.numero1 - this.numero2;
        case 'multiplicacao':
          return this.numero1 * this.numero2;
        case 'divisao':
          return this.numero2 !== 0 ? this.numero1 / this.numero2 : 'Erro: Divisão por zero';
        default:
          return 0;
      }
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.calculator {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 2px solid #ccc;
  border-radius: 10px;
  background-color: #f9f9f9;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
}

.inputs {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

input {
  width: 45%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.operation {
  margin-bottom: 20px;
}

select {
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
}

.result {
  margin-top: 20px;
  font-size: 20px;
  font-weight: bold;
}
</style>
