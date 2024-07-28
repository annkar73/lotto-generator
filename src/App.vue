<script setup lang="ts">
import { ref } from 'vue';
import LottoGenerator from './components/LottoGenerator.vue';
import EurojackpottGenerator from './components/EurojackpotGenerator.vue';
import KenoGenerator from './components/KenoGenerator.vue';


    const currentGenerator = ref<'lotto' | 'eurojackpot' | 'keno'>('lotto');
</script>

<template>
  <div id="app">
    <h1>Lottery Numbers Generators</h1>
    <div class="buttons">
      <button @click="currentGenerator = 'lotto'">Lotto</button>
      <button @click="currentGenerator = 'eurojackpot'">Eurojackpot</button>
      <button @click="currentGenerator = 'keno'">Keno</button>
    </div>
    <div class="generator">
      <LottoGenerator v-if="currentGenerator === 'lotto'" />
      <EurojackpottGenerator v-if="currentGenerator === 'eurojackpot'" />
      <KenoGenerator v-if="currentGenerator === 'keno'" />
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
.buttons {
  margin-bottom: 20px;
}
.buttons button {
  margin: 5px;
}
.generator {
  margin-top: 20px;
}
</style>
