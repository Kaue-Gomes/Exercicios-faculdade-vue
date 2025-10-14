<template>
  <div class="lista-tarefas-container">
    <h2> Lista de Tarefas</h2>
    
    <div class="adicionar-tarefa">
      <input 
        v-model="novaTarefa" 
        @keyup.enter="adicionarTarefa"
        type="text" 
        placeholder="Digite uma nova tarefa..."
        class="input-tarefa"
      >
      <button @click="adicionarTarefa" class="btn-adicionar">
        Adicionar
      </button>
    </div>
    
    <div class="contador-tarefas">
      <p>Total de tarefas: <strong>{{ totalTarefas }}</strong></p>
    </div>
    
    <div v-if="tarefas.length === 0" class="vazio">
      <p>Nenhuma tarefa adicionada ainda. Comece adicionando uma!</p>
    </div>
    
    <ul v-else class="lista">
      <li 
        v-for="(tarefa, index) in tarefas" 
        :key="index"
        class="tarefa-item"
      >
        <span class="tarefa-texto">{{ tarefa }}</span>
        <button @click="removerTarefa(index)" class="btn-remover">
          ✕
        </button>
      </li>
    </ul>
    
    <button 
      v-if="tarefas.length > 0" 
      @click="limparTodas" 
      class="btn-limpar"
    >
      Limpar Todas
    </button>
  </div>
</template>

<script>
export default {
  name: 'ListaTarefas',
  data() {
    return {
      novaTarefa: '',
      tarefas: []
    }
  },
  computed: {
    totalTarefas() {
      return this.tarefas.length
    }
  },
  methods: {
    adicionarTarefa() {
      if (this.novaTarefa.trim() !== '') {
        this.tarefas.push(this.novaTarefa.trim())
        this.novaTarefa = ''
      }
    },
    removerTarefa(index) {
      this.tarefas.splice(index, 1)
    },
    limparTodas() {
      if (confirm('Tem certeza que deseja limpar todas as tarefas?')) {
        this.tarefas = []
      }
    }
  }
}
</script>

<style scoped>
.lista-tarefas-container {
  max-width: 600px;
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

.adicionar-tarefa {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.input-tarefa {
  flex: 1;
  padding: 10px;
  font-size: 14px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.btn-adicionar {
  padding: 10px 20px;
  font-size: 14px;
  border: none;
  border-radius: 4px;
  background: #4caf50;
  color: white;
  cursor: pointer;
}

.btn-adicionar:hover {
  opacity: 0.8;
}

.contador-tarefas {
  background: #f5f5f5;
  padding: 10px;
  border-radius: 4px;
  text-align: center;
  margin-bottom: 20px;
}

.contador-tarefas p {
  margin: 0;
  font-size: 14px;
  color: #333;
}

.vazio {
  text-align: center;
  padding: 30px 20px;
  background: #f5f5f5;
  border-radius: 4px;
  color: #666;
}

.lista {
  list-style: none;
  padding: 0;
  margin: 0;
}

.tarefa-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f9f9f9;
  padding: 12px;
  margin-bottom: 8px;
  border-radius: 4px;
  border: 1px solid #eee;
}

.tarefa-texto {
  color: #333;
  font-size: 14px;
  flex: 1;
}

.btn-remover {
  background: #f44336;
  color: white;
  border: none;
  border-radius: 4px;
  width: 24px;
  height: 24px;
  font-size: 14px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn-remover:hover {
  opacity: 0.8;
}

.btn-limpar {
  width: 100%;
  padding: 10px;
  margin-top: 15px;
  font-size: 14px;
  border: none;
  border-radius: 4px;
  background: #ff9800;
  color: white;
  cursor: pointer;
}

.btn-limpar:hover {
  opacity: 0.8;
}
</style>

