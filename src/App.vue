<script setup lang="ts">
import { ref } from 'vue';
import NavMenu from './components/NavMenu.vue';
import FirstPage from './components/FirstPage.vue';
import LottoGenerator from './components/LottoGenerator.vue';
import EurojackpottGenerator from './components/EurojackpotGenerator.vue';
import VikinglottoGenerator from './components/VikinglottoGenerator.vue';
import KenoGenerator from './components/KenoGenerator.vue';

const currentGenerator = ref<'home' | 'lotto' | 'eurojackpot' | 'vikinglotto' | 'keno'>('home');

const updateGenerator = (newGenerator: 'home' | 'lotto' | 'eurojackpot' | 'vikinglotto' | 'keno') => {
  currentGenerator.value = newGenerator;
};

</script>

<template>
<div id="app">
  <div class="header">
    <h1>Slumpa spelrader</h1>
    <h2>för flera olika spel</h2>
  </div>
    <div class="container">
      <NavMenu :current="currentGenerator" @update:generator="updateGenerator" />

    <div class="generator">
      <FirstPage v-if="currentGenerator === 'home'" />
      <LottoGenerator v-if="currentGenerator === 'lotto'" />
      <EurojackpottGenerator v-if="currentGenerator === 'eurojackpot'" />
      <VikinglottoGenerator v-if="currentGenerator === 'vikinglotto'" />
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
  left: 0;
  right: 0;
  background-color: #9c441f;
  text-align: center;
  width: 100vw;
  height: 100px;
  margin: 0;
  box-sizing: border-box;
  z-index: 1000;
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
  height: calc(100vh - 100px);
  overflow: hidden;
  margin-top: 100px;
}
.nav-menu {
  width: 200px;
  background-color: #fff3da;
  padding: 15px;
  overflow: auto;
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
    width: 100%;
    height: auto;
  }
  .container {
    flex-direction: column;
    align-items: center;
    margin-top: 100px;
    height: calc(100vh - 100px);
  }

  .generator {
    width: 100%;
  }
}
</style>
