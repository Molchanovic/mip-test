<script setup lang="ts"></script>

<template>
  <div class="text-block">
    <slot></slot>
  </div>
</template>

<style lang="scss">
.text-block {
  margin-bottom: calc(1em + 0.01vw);

  p {
    margin-bottom: 5px;
  }
  p:nth-child(even) {
    padding-left: 10%;
  }
}
</style>
