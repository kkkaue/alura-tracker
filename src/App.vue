<script lang="ts">
import { defineComponent } from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import type ITarefa from '@/interfaces/ITarefa'
import Box from './components/Box.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
},
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  methods: {
    adicionarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    }
  }
})
</script>

<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarters">
      <Formulario @adicionarTarefa="adicionarTarefa" />
      <div class="lista">
        <Tarefa 
          v-for="tarefa in tarefas" 
          :key="tarefa.descricao" 
          :tarefa="tarefa"
        />
        <Box v-if="listaEstaVazia">
          Você não está muito produtivo hoje, hein?
        </Box>
      </div>
    </div>
  </main>
</template>

<style scoped>
.lista {
  padding: 1.25rem;
}
</style>
