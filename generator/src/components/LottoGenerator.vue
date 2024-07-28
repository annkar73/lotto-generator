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
    <h2>Lotto Generator</h2>
    <button @click="generateLottoNumbers">Generate Lotto Numbers</button>
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
.number-list {
    display: inline;
    padding: 0;
  list-style-type: none;
}

.number-list li {
    display: inline;
}
</style>
