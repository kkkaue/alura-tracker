<script lang="ts">
import { defineComponent } from 'vue'
import BarraLateral from './components/BarraLateral.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
},
  data() {
    return {
      modoEscuroAtivo: false,
    }
  },
  methods: {
    alterarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
})
</script>

<template>
  <main :class="{ 'modo-escuro': modoEscuroAtivo }" class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral @temaAlterado="alterarTema" />
    </div>
    <div class="column is-three-quarters conteudo">
      <RouterView></RouterView>
    </div>
  </main>
</template>

<style scoped>
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background: var(--bg-primario);
  color: var(--texto-primario);
}
</style>
