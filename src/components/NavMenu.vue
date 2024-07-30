<script setup lang="ts">
import { defineEmits } from 'vue'

const emits = defineEmits(['update:generator'])

const setGenerator = (generator: 'lotto' | 'eurojackpot' | 'keno') => {
  emits('update:generator', generator)
}
</script>

<template>
  <div class="nav-menu">
    <h2>Välj spel</h2>
    <button @click="() => setGenerator('lotto')">Lotto</button>
    <button @click="() => setGenerator('eurojackpot')">Eurojackpot</button>
    <button @click="() => setGenerator('keno')">Keno</button>
  </div>
</template>

<style scoped>
.nav-menu {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: none;
  padding: 1px;
}

.nav-menu h2 {
    margin-bottom: 10px;
    text-transform: uppercase;
    font-weight: bold;
}

.nav-menu button {
  height: 40px;
  width: 100%;
  margin-bottom: 5px;
  padding: 5px 5px;
  background-color: #646544;
  color: #fff3da;
  text-transform: uppercase;
  font-size: large;
  font-weight: bold;
  border-radius: 5px;
}
.nav-menu button:hover {
    background-color: #7b3415;
}
</style>
