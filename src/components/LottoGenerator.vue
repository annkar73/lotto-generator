<script setup lang="ts">
import { ref } from 'vue'

const lottoNumbers = ref<number[]>([])

const generateLottoNumbers = () => {
  const numbers = new Set<number>()
  while (numbers.size < 7) {
    const num = Math.floor(Math.random() * 35) + 1 //Lotto numbers between 1 and 35
    numbers.add(num)
  }
  lottoNumbers.value = Array.from(numbers).sort((a, b) => a - b)
}
</script>

<template>
  <div>
    <h2>Lotto</h2>
    <button @click="generateLottoNumbers">Slumpa nummer</button>
    <div v-if="lottoNumbers.length">
      <ul class="number-list">
        <li v-for="(number, index) in lottoNumbers" :key="number">{{ number }}
            <span v-if="index < lottoNumbers.length - 1">, </span>
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
    display: inline;
    padding: 0;
  list-style-type: none;
  padding: 5px;
  margin: 15px;
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
