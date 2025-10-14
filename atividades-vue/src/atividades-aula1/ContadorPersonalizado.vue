<template>
  <div class="contador-container">
    <h2>Contador Personalizado</h2>
    <div class="contador-display">
      <h1>{{ contador }}</h1>
    </div>
    
    <div v-if="contador >= 10" class="mensagem-sucesso">
       Parabéns! Você chegou a 10!
    </div>
    
    <div class="botoes-container">
      <button @click="incrementar(1)" class="btn btn-incrementar">+1</button>
      <button @click="decrementar(1)" class="btn btn-decrementar" :disabled="contador === 0">-1</button>
      <button @click="incrementar(5)" class="btn btn-incrementar">+5</button>
      <button @click="decrementar(5)" class="btn btn-decrementar" :disabled="contador < 5">-5</button>
    </div>
    
    <button @click="resetar" class="btn btn-reset">Resetar</button>
  </div>
</template>

<script>
export default {
  name: 'ContadorPersonalizado',
  data() {
    return {
      contador: 0
    }
  },
  methods: {
    incrementar(valor) {
      this.contador += valor
    },
    decrementar(valor) {
      // Não permite valores negativos
      if (this.contador - valor >= 0) {
        this.contador -= valor
      }
    },
    resetar() {
      this.contador = 0
    }
  }
}
</script>

<style scoped>
.contador-container {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  border: 1px solid #ddd;
  text-align: center;
}

h2 {
  margin-bottom: 20px;
  font-size: 20px;
  color: #333;
}

.contador-display {
  background: #f5f5f5;
  padding: 20px;
  border-radius: 4px;
  margin: 20px 0;
}

.contador-display h1 {
  font-size: 48px;
  margin: 0;
  color: #333;
}

.mensagem-sucesso {
  background: #4caf50;
  color: white;
  padding: 10px;
  border-radius: 4px;
  margin: 15px 0;
}

.botoes-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  margin: 20px 0;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn:hover:not(:disabled) {
  opacity: 0.8;
}

.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.btn-incrementar {
  background: #4caf50;
  color: white;
}

.btn-decrementar {
  background: #f44336;
  color: white;
}

.btn-reset {
  width: 100%;
  background: #ff9800;
  color: white;
  margin-top: 10px;
}
</style>

