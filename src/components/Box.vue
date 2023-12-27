<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BoxComponent'
})
</script>

<template>
  <div class="box has-text-weight-bold">
    <slot></slot>
  </div>
</template>

<style scoped>
.box {
  background: #FAF0CA;
}
</style>