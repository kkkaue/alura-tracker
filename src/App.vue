<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarters">
      <Formulario />
    </div>
  </main>
</template>

<script setup lang="ts">
import { defineComponent } from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue';

defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario
  }
})
</script>

<style scoped></style>
