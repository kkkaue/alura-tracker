<script lang="ts">
import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'
import IconButton from './IconButton.vue'

export default defineComponent({
  name: 'CronometroComponent',
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    }
  },
  methods: {
    iniciarTarefa(): void {
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos++
      }, 1000)
    },
    finalizarTarefa(): void {
      this.cronometroRodando = false
      clearInterval(this.cronometro)

      this.$emit('temporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    }
  },
  components: {
    Cronometro,
    IconButton
  },
  emits: ['temporizadorFinalizado']
})
</script>

<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <IconButton
      classeDoIcone="fas fa-play"
      label="start"
      :desabilitado="cronometroRodando"
      @clicado="iniciarTarefa"
    />
    <IconButton
      classeDoIcone="fas fa-stop"
      label="stop"
      :desabilitado="!cronometroRodando"
      @clicado="finalizarTarefa"
    />
  </div>
</template>
