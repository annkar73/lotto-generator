<script setup lang="ts">
import { ref } from 'vue';

const eurojackpotNumbers = ref<number[]>([]);
const eurojackpotSpecial = ref<number[]>([]);

const generateEurojackpotNumbers = () => {
  const mainNumbers = new Set<number>();
  while (mainNumbers.size < 5) {
    const num = Math.floor(Math.random() * 50) + 1; // Eurojackpot numbers between 1 and 50
    mainNumbers.add(num);
  }
  eurojackpotNumbers.value = Array.from(mainNumbers).sort((a, b) => a - b);

  const specialNumbers = new Set<number>();
  while (specialNumbers.size < 2) {
    const num = Math.floor(Math.random() * 10) + 1; // Eurojackpot special numbers between 1 and 10
    specialNumbers.add(num);
  }
  eurojackpotSpecial.value = Array.from(specialNumbers).sort((a, b) => a - b);
};
</script>

<template>
  <div>
    <h2>Eurojackpot</h2>
    <button @click="generateEurojackpotNumbers">Slumpa nummer</button>
    <div v-if="eurojackpotNumbers.length">
      <h3>Nummer:</h3>
      <ul class="number-list">
        <li v-for="(number, index) in eurojackpotNumbers" :key="number">
          {{ number }}<span v-if="index < eurojackpotNumbers.length - 1">, </span>
        </li>
      </ul>
      <h3>Stjärnnummer:</h3>
      <ul class="number-list">
        <li v-for="(number, index) in eurojackpotSpecial" :key="number">
          {{ number }}<span v-if="index < eurojackpotSpecial.length - 1">, </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>

h2 {
  text-transform: uppercase;
  font-weight: bold;
}
h3 {
  font-weight: bold;
}
.number-list {
    display: inline;
    padding: 0;
  list-style-type: none;
}

.number-list li {
    display: inline;
    font-weight: 600;
}
button {
  margin-bottom: 15px;
  margin-top: 15px;
  background-color: #9c441f;
  color: #fff3da;
  border: none;
  border-radius: 5px;
  width:200px;
  height: 45px;
  text-transform: uppercase;
  font-size: large;
  font-weight: bold;
}

button:hover {
  background-color: #646544;
}
</style>
