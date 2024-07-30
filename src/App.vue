<script setup lang="ts">
import { ref } from 'vue';
import NavMenu from './components/NavMenu.vue';
import FirstPage from './components/FirstPage.vue';
import LottoGenerator from './components/LottoGenerator.vue';
import EurojackpottGenerator from './components/EurojackpotGenerator.vue';
import KenoGenerator from './components/KenoGenerator.vue';

const currentGenerator = ref<'home' | 'lotto' | 'eurojackpot' | 'keno'>('home');

const updateGenerator = (newGenerator: 'home' | 'lotto' | 'eurojackpot' | 'keno') => {
  currentGenerator.value = newGenerator;
};

</script>

<template>
<div id="app">
  <div class="header">
    <h1>Slumpa spelrader</h1>
    <h2>för Lotto, Eurojackpot och Keno</h2>
  </div>
    <div class="container">
      <NavMenu @update:generator="updateGenerator" />

    <div class="generator">
      <FirstPage v-if="currentGenerator === 'home'" />
      <LottoGenerator v-if="currentGenerator === 'lotto'" />
      <EurojackpottGenerator v-if="currentGenerator === 'eurojackpot'" />
      <KenoGenerator v-if="currentGenerator === 'keno'" />
    </div>
  </div>
  </div>
  </template>

<style scoped>
html, body {
  margin: 0;
  padding: 0;
  overflow: hidden;
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  background-color: #fff3da;
  color: #36251b;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
}
.header {
  position: fixed;
  top: 0;
  background-color: #9c441f;
  width: 100vw;
  margin: 0;
  box-sizing: border-box;
  z-index: 1;
}
h1, h2 {
  background-color: #9c441f;
  color: #fff3da;
  padding: 0 15px;
  margin: 0;
  width: 100vw;
}
h1 {
  font-weight: 600;
  text-transform: uppercase;

}
.container {
  display: flex;
  flex: 1;
  width: 100%;
  height: calc(100vh - 80px);
  overflow: hidden;
  margin-top: 80px;
}
.nav-menu {
  width: 200px;
  background-color: #fff3da;
  padding: 15px;
  align-items: center;
}
.generator {
  flex: 1;
  padding: 20px;
  display: flex;
  justify-content: center;
  overflow: auto;
}

@media (max-width: 468px) {
  .nav-menu {
    border: none;
    width: 100%;
  }
  .container {
    flex-direction: column;
    align-items: center;
    margin-top: 80px;
    height: calc(100vh - 80px);
  }

  .generator {
    flex: 1;
    width: 100%;
  }
}
</style>
