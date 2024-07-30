<script setup lang="ts">
import { ref } from 'vue';

const kenoNumbers = ref<number[]>([]);
const numberOfNumbers = ref<number>(10); // Default number of Keno numbers to generate

const generateKenoNumbers = () => {
  const numbers = new Set<number>();
  while (numbers.size < numberOfNumbers.value) {
    const num = Math.floor(Math.random() * 70) + 1; // Keno numbers between 1 and 70
    numbers.add(num);
  }
  kenoNumbers.value = Array.from(numbers).sort((a, b) => a - b);
};
</script>

<template>
  <div>
    <h2>Keno</h2>
    <div class="input-group">
      <label for="number-of-numbers">Antal nummer (1-11):</label>
      <input for="number of numbers" type="number" v-model="numberOfNumbers" min="1" max="11">
    </div>
    <button @click="generateKenoNumbers">Slumpa nummer</button>
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
h2 {
  text-transform: uppercase;
  font-weight: bold;
}
.number-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(20px, 1fr));
    gap: 5px;
    padding: 5px;
  list-style-type: none;
  margin: 15px;
  justify-content: center;
}

.number-list li {
    display: inline;
    font-weight: 600;
    background-color: #fff3da;
    color: #36251b;
    padding: 5px;
}
button {
  margin-bottom: 15px;
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

.input-group {
  margin-bottom: 15px;
}
label {
  font-weight: bold;
}
input {
  width: 50px;
  margin-left: 10px;
}
</style>
