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
    <h1>Lottery Numbers Generators</h1>
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
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  margin-bottom: 45px;
}
.container {
  display: flex;
}
.nav-menu {
  flex: 1;
}
.generator {
  flex: 3;
  margin-top: 20px;
}
</style>
