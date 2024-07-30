<script setup lang="ts">
import { defineEmits } from 'vue'

const emits = defineEmits(['update:generator'])

const setGenerator = (generator: 'lotto' | 'eurojackpot' | 'keno') => {
  emits('update:generator', generator)
}
</script>

<template>
  <div class="nav-menu">
    <button @click="() => setGenerator('home')" id="home-btn">Hem</button>
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
  margin-top: 10px;
  padding: 1px;
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
#home-btn {
    background-color: #9c441f;
}
#home-btn:hover {
    background-color: #646544;
}
@media (max-width: 768px) {
  .nav-menu {
    width: 100%;
    border-right: none;
    display: flex;
    justify-content: space-around;
  }

  .nav-menu button {
    margin-bottom: 5px;
    padding: 10px;
    width: 100%;
    border: none;
  }
}
</style>
