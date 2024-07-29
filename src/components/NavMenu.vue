<script setup lang="ts">
import { defineEmits } from 'vue';

const emits = defineEmits(['update:generator']);

const setGenerator = (generator: 'lotto' | 'eurojackpot' | 'keno') => {
  emits('update:generator', generator);
};
</script>

<template>
<div class="nav-menu">
    <button @click="() => setGenerator('lotto')">Lotto</button>
    <button @click="() => setGenerator('eurojackpot')">Eurojackpott</button>
    <button @click="() => setGenerator('keno')">Keno</button>
  </div>
  </template>

<style scoped>
.nav-menu {
    display: flex;
    flex-direction: column;
  margin-bottom: 20px;
}

.nav-menu button {
  margin: 5px;
}
</style>