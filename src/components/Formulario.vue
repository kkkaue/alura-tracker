<script lang="ts">
import { defineComponent } from 'vue'
import Temporizador from './Temporizador.vue';

export default defineComponent({
    name: 'FormularioComponent',
    data() {
      return {
        descricao: '',
      }
    },
    components: { 
      Temporizador
    },
    methods: {
      finalizarTarefa(tempoEmSegundos: number) : void {
        this.$emit('adicionarTarefa', {
          duracaoEmSegundos: tempoEmSegundos,
          descricao: this.descricao,
        });
        this.descricao = '';
      }
    },
    emits: ['adicionarTarefa']
})
</script>

<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para a criação de uma nova tarefa"
      >
        <input 
          type="text" 
          class="input" 
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <Temporizador @temporizador-finalizado="finalizarTarefa" />
      </div>
    </div>
  </div>
</template>