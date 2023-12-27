<script lang="ts">
import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'

export default defineComponent({
  name: 'TarefaComponent',
  data() {
    return {
      tempoEmSegundos: 0
    }
  },
  components: { Cronometro }
})
</script>

<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">Descição da tarefa</div>
      <div class="column">
        <Cronometro :tempoEmSegundos="tempoEmSegundos" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.box {
  background: #FAF0CA;
}
</style>