<template>
  <div class="calculadora-imc-container">
    <h2> Calculadora de IMC</h2>
    
    <div class="formulario">
      <div class="input-group">
        <label for="peso">Peso (kg):</label>
        <input 
          id="peso"
          v-model.number="peso" 
          type="number" 
          step="0.1"
          min="0"
          placeholder="Ex: 70.5"
          class="input-campo"
        >
      </div>
      
      <div class="input-group">
        <label for="altura">Altura (m):</label>
        <input 
          id="altura"
          v-model.number="altura" 
          type="number" 
          step="0.01"
          min="0"
          placeholder="Ex: 1.75"
          class="input-campo"
        >
      </div>
    </div>
    
    <div v-if="imcCalculado !== null" class="resultado">
      <div class="imc-valor" :class="classificacaoClass">
        <p class="label">Seu IMC:</p>
        <h1>{{ imcCalculado }}</h1>
      </div>
      
      <div class="classificacao" :class="classificacaoClass">
        <p class="label">Classificação:</p>
        <h3>{{ classificacao }}</h3>
      </div>
    </div>
    
    <div v-else class="instrucao">
      <p>Digite seu peso e altura para calcular o IMC</p>
    </div>
    
    <div class="tabela-referencia">
      <h4>Tabela de Referência</h4>
      <ul>
        <li class="baixo-peso">Abaixo de 18.5: Baixo peso</li>
        <li class="normal">18.5 - 24.9: Peso normal</li>
        <li class="sobrepeso">25.0 - 29.9: Sobrepeso</li>
        <li class="obesidade-1">30.0 - 34.9: Obesidade grau I</li>
        <li class="obesidade-2">35.0 - 39.9: Obesidade grau II</li>
        <li class="obesidade-3">Acima de 40: Obesidade grau III</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculadoraIMC',
  data() {
    return {
      peso: null,
      altura: null
    }
  },
  computed: {
    imcCalculado() {
      if (this.peso > 0 && this.altura > 0) {
        const imc = this.peso / (this.altura * this.altura)
        return imc.toFixed(1)
      }
      return null
    },
    classificacao() {
      if (this.imcCalculado === null) return ''
      
      const imc = parseFloat(this.imcCalculado)
      
      if (imc < 18.5) return 'Baixo peso'
      if (imc >= 18.5 && imc < 25) return 'Peso normal'
      if (imc >= 25 && imc < 30) return 'Sobrepeso'
      if (imc >= 30 && imc < 35) return 'Obesidade grau I'
      if (imc >= 35 && imc < 40) return 'Obesidade grau II'
      return 'Obesidade grau III'
    },
    classificacaoClass() {
      if (this.imcCalculado === null) return ''
      
      const imc = parseFloat(this.imcCalculado)
      
      if (imc < 18.5) return 'baixo-peso'
      if (imc >= 18.5 && imc < 25) return 'normal'
      if (imc >= 25 && imc < 30) return 'sobrepeso'
      if (imc >= 30 && imc < 35) return 'obesidade-1'
      if (imc >= 35 && imc < 40) return 'obesidade-2'
      return 'obesidade-3'
    }
  }
}
</script>

<style scoped>
.calculadora-imc-container {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  border: 1px solid #ddd;
}

h2 {
  text-align: center;
  margin-bottom: 20px;
  font-size: 20px;
  color: #333;
}

.formulario {
  margin-bottom: 20px;
}

.input-group {
  margin-bottom: 15px;
}

.input-group label {
  display: block;
  margin-bottom: 5px;
  font-size: 14px;
  color: #333;
}

.input-campo {
  width: 100%;
  padding: 10px;
  font-size: 14px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;
}

.instrucao {
  text-align: center;
  padding: 20px;
  background: #f5f5f5;
  border-radius: 4px;
  color: #666;
  margin-bottom: 20px;
}

.resultado {
  margin-bottom: 20px;
}

.imc-valor, .classificacao {
  background: #f9f9f9;
  padding: 15px;
  border-radius: 4px;
  text-align: center;
  margin-bottom: 10px;
  border: 1px solid #eee;
}

.label {
  margin: 0 0 5px 0;
  font-size: 12px;
  text-transform: uppercase;
  color: #666;
}

.imc-valor h1 {
  margin: 0;
  font-size: 36px;
}

.classificacao h3 {
  margin: 0;
  font-size: 18px;
}

/* Cores por classificação */
.baixo-peso {
  color: #2196f3 !important;
}

.normal {
  color: #4caf50 !important;
}

.sobrepeso {
  color: #ff9800 !important;
}

.obesidade-1 {
  color: #ff5722 !important;
}

.obesidade-2 {
  color: #f44336 !important;
}

.obesidade-3 {
  color: #9c27b0 !important;
}

.tabela-referencia {
  background: #f5f5f5;
  padding: 15px;
  border-radius: 4px;
}

.tabela-referencia h4 {
  margin-top: 0;
  margin-bottom: 10px;
  text-align: center;
  font-size: 14px;
  color: #333;
}

.tabela-referencia ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.tabela-referencia li {
  padding: 8px;
  margin-bottom: 5px;
  background: white;
  border-radius: 4px;
  font-size: 12px;
  border-left: 3px solid;
}

.tabela-referencia li.baixo-peso {
  border-left-color: #2196f3;
}

.tabela-referencia li.normal {
  border-left-color: #4caf50;
}

.tabela-referencia li.sobrepeso {
  border-left-color: #ff9800;
}

.tabela-referencia li.obesidade-1 {
  border-left-color: #ff5722;
}

.tabela-referencia li.obesidade-2 {
  border-left-color: #f44336;
}

.tabela-referencia li.obesidade-3 {
  border-left-color: #9c27b0;
}
</style>

