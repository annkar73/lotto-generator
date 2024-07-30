<script setup lang="ts">
import { ref } from 'vue';
import NavMenu from './components/NavMenu.vue';
import LottoGenerator from './components/LottoGenerator.vue';
import EurojackpottGenerator from './components/EurojackpotGenerator.vue';
import KenoGenerator from './components/KenoGenerator.vue';

const currentGenerator = ref<'lotto' | 'eurojackpot' | 'keno'>('lotto');

const updateGenerator = (newGenerator: 'lotto' | 'eurojackpot' | 'keno') => {
  currentGenerator.value = newGenerator;
};

</script>

<template>
<div id="app">
    <h1>Slumpa nummer</h1>
    <h2>För Lotto, Eurojackpot och Keno</h2>
    <div class="container">
      <NavMenu @update:generator="updateGenerator" />

    <div class="generator">
      <LottoGenerator v-if="currentGenerator === 'lotto'" />
      <EurojackpottGenerator v-if="currentGenerator === 'eurojackpot'" />
      <KenoGenerator v-if="currentGenerator === 'keno'" />
    </div>
  </div>
  </div>
  </template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  background-color: #fff3da;
  color: #36251b;
  margin-top: 20px;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
}
h1 {
  margin-bottom: 5px;
  font-weight: 600;
  text-transform: uppercase;
}
h2 {
  margin-bottom: 25px;
}
.container {
  display: flex;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.nav-menu {
  width: 200px;
  background-color: #fff3da;
  padding: 15px;
  margin: 1px;
}
.generator {
  flex: 1;
  padding: 20px;
  display: flex;
  justify-content: center;
  overflow: hidden;
}

@media (max-width: 468px) {
  .nav-menu {
    border: none;
  }
  .container {
    flex-direction: column;
    align-items: center;
  }

  .generator {
    flex: 1;
    width: 100%;
  }
}
</style>
