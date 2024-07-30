<script setup lang="ts">
import { ref } from 'vue';

const vikinglottoNumbers = ref<number[]>([]);
const vikinglottoSpecial = ref<number | null>(null);

const generateVikinglottoNumbers = () => {
  const mainNumbers = new Set<number>();
  while (mainNumbers.size < 6) {
    const num = Math.floor(Math.random() * 48) + 1; // Vikinglotto numbers between 1 and 48
    mainNumbers.add(num);
  }
  vikinglottoNumbers.value = Array.from(mainNumbers).sort((a, b) => a - b);

  vikinglottoSpecial.value = Math.floor(Math.random() * 6) + 1; // Vikinglotto special number between 1 and 6
};

generateVikinglottoNumbers();
</script>

<template>
  <div>
    <h2>Vikinglotto</h2>
    <button @click="generateVikinglottoNumbers">Slumpa nummer</button>
    <div v-if="vikinglottoNumbers.length">
      <h3>Nummer:</h3>
      <ul class="number-list">
        <li v-for="(number, index) in vikinglottoNumbers" :key="number">
          {{ number }}<span v-if="index < vikinglottoNumbers.length - 1">, </span>
        </li>
      </ul>
      <h3>Vikingnummer:</h3>
      <ul class="number-list">
        <li v-if="vikinglottoSpecial !== null">{{ vikinglottoSpecial }}</li>
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
  width: 200px;
  height: 45px;
  text-transform: uppercase;
  font-size: large;
  font-weight: bold;
}

button:hover {
  background-color: #646544;
}
</style>
