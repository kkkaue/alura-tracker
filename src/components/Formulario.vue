<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'FormularioComponent',
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
    }
  },
  computed: {
    tempoDecorrido() : string {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8)
    }
  },
  methods: {
    iniciarTarefa() {
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos++
      }, 1000)
      console.log('iniciar tarefa')
    },
    finalizarTarefa() {
      clearInterval(this.cronometro)
      console.log('finalizar tarefa')
    }
  }
})
</script>

<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">
          <section>
            <strong>
              {{ tempoDecorrido }}
            </strong>
          </section>
          <button class="button" @click="iniciarTarefa">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="finalizarTarefa">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>