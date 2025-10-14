<script setup>
import ContadorPersonalizado from './atividades-aula1/ContadorPersonalizado.vue'
import ListaTarefas from './atividades-aula1/ListaTarefas.vue'
import CalculadoraIMC from './atividades-aula1/CalculadoraIMC.vue'
</script>

<template>
  <div class="app-container">
    <header>
      <h1> Exercícios - Aula 1 Vue.js</h1>
      <p>Prática dos conceitos fundamentais do Vue.js</p>
    </header>

    <main>
      <section class="exercicio">
        <h2>Exercício 1: Contador Personalizado</h2>
        <ContadorPersonalizado />
      </section>

      <section class="exercicio">
        <h2>Exercício 2: Lista de Tarefas</h2>
        <ListaTarefas />
      </section>

      <section class="exercicio">
        <h2>Exercício 3: Calculadora de IMC</h2>
        <CalculadoraIMC />
      </section>
    </main>

  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background: #f0f0f0;
  min-height: 100vh;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>

<style scoped>
.app-container {
  min-height: 100vh;
  padding: 20px;
}

header {
  text-align: center;
  background: white;
  padding: 30px 20px;
  margin-bottom: 30px;
  border-radius: 8px;
  border: 1px solid #ddd;
  max-width: 1200px;
  margin: 0 auto 30px;
}

header h1 {
  font-size: 28px;
  margin-bottom: 10px;
  color: #333;
}

header p {
  font-size: 14px;
  color: #666;
}

main {
  max-width: 1200px;
  margin: 0 auto;
}

.exercicio {
  margin-bottom: 40px;
}

.exercicio > h2 {
  color: #333;
  text-align: center;
  margin-bottom: 15px;
  font-size: 18px;
  background: white;
  padding: 15px;
  border-radius: 8px;
  border: 1px solid #ddd;
}
</style>
