<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IconButtonComponent',
  props: {
    classeDoIcone: {
      type: String,
      required: true
    },
    desabilitado: {
      type: Boolean,
      default: false
    },
    label: {
      type: String,
      required: true
    }
  },
  methods: {
    clicado() : void {
      this.$emit('clicado')
    }
  },
  emits: ['clicado']
})
</script>

<template>
  <button class="button" @click="clicado" :disabled="desabilitado">
    <span class="icon">
      <i :class="classeDoIcone"></i>
    </span>
    <span>{{ label }}</span>
  </button>
</template>
