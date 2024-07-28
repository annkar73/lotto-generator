<script setup lang="ts">
import { ref } from 'vue';

const kenoNumbers = ref<number[]>([]);

const generateKenoNumbers = () => {
  const numbers = new Set<number>();
  while (numbers.size < 10) {
    const num = Math.floor(Math.random() * 70) + 1; // Keno numbers between 1 and 70
    numbers.add(num);
  }
  kenoNumbers.value = Array.from(numbers).sort((a, b) => a - b);
};
</script>

<template>
  <div>
    <h2>Keno Generator</h2>
    <button @click="generateKenoNumbers">Generate Keno Numbers</button>
    <div v-if="kenoNumbers.length">
      <ul class="number-list">
        <li v-for="(number, index) in kenoNumbers" :key="number">
          {{ number }}<span v-if="index < kenoNumbers.length - 1">, </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.number-list {
  display: inline;
  padding: 0;
  list-style-type: none;
}

.number-list li {
  display: inline;
}
</style>
