<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'
defineProps({ state: Boolean, id: Number })
defineEmits(['changeState'])
</script>

<template>
  <span
    :class="{ opacity: !state }"
    @click="$emit('changeState', id)"
  ></span>
</template>

<style lang="scss">
span {
  width: calc(0.5em + 0.5vw);
  height: calc(0.5em + 0.5vw);
  background: #000;
  border: 1px solid #000;

  &.opacity {
    background: transparent;
  }
}
</style>
