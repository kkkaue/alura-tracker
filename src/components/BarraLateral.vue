<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BarraLateral',
  data() {
    return {
      temaEscuroAtivo: false
    }
  },
  computed: {
    textoBotao(): string {
      return this.temaEscuroAtivo ? 'Ativar modo claro' : 'Ativar modo escuro'
    }
  },
  methods: {
    alterarTema() {
      this.temaEscuroAtivo = !this.temaEscuroAtivo
      this.$emit('temaAlterado', this.temaEscuroAtivo)
    }
  },
  emits: [
    'temaAlterado'
  ]
})
</script>

<template>
  <header>
    <h1>
      <img src="..\assets\images\logo.png" alt="">
    </h1>
    <button class="button" @click="alterarTema">
      {{ textoBotao }}
    </button>
  </header>
</template>

<style scoped>
  header {
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
  }
  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>