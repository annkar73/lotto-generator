<script setup lang="ts">
import { defineEmits, defineProps } from 'vue'

const emits = defineEmits(['update:generator'])
const props = defineProps({
    current: {
        type: String, 
        required: true,
    }
});

const setGenerator = (generator: 'lotto' | 'eurojackpot' | 'keno') => {
  emits('update:generator', generator)
}
</script>

<template>
  <div class="nav-menu">
    <button @click="() => setGenerator('home')" id="home-btn">Hem</button>
    <button :class="{ active: props.current === 'lotto'}" @click="setGenerator('lotto')">Lotto</button>
    <button :class="{ active: props.current === 'eurojackpot'}" @click="setGenerator('eurojackpot')">Eurojackpot</button>
    <button :class="{ active: props.current === 'keno'}" @click="setGenerator('keno')">Keno</button>
  </div>
</template>

<style scoped>
.nav-menu {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-left: none;
  margin-top: 10px;
  padding: 1px;
}

.nav-menu button {
  height: 40px;
  width: 100%;
  margin-bottom: 5px;
  padding: 5px 5px;
  background-color: #646544;
  color: #fff3da;
  text-transform: uppercase;
  font-size: large;
  font-weight: bold;
  border-radius: 5px;
}
.nav-menu button:hover {
    background-color: #fff3da;
    border: 3px solid #9c441f;
    color: #9c441f;
}

.nav-menu .active {
    background-color: #9c441f;

}
#home-btn {
    background-color: #36251b;

}
#home-btn:hover {
   background-color: #fff3da;
    border: 3px solid #36251b;
    color: #36251b;
}
@media (max-width: 768px) {
  .nav-menu {
    width: 100%;
    border-right: none;
    display: flex;
    justify-content: space-around;
  }

  .nav-menu button {
    margin-bottom: 5px;
    padding: 10px;
    width: 100%;
    border: none;
  }
}
</style>
