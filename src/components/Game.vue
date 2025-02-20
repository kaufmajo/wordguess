<script setup>
import { ref } from 'vue'
import Letter from './Letter.vue'
import Placeholder from './Placeholder.vue'

const alphabet = Array.from({ length: 26 }, (_, i) => String.fromCharCode(97 + i));
const word = 'hello';
const guesses = ref(Array.from({ length: word.length }, () => ''));
const maxGuesses = 6;

</script>

<template>
  
  <div class="placeholder">
    <Placeholder v-for="char in guesses" :key="char" :char="char" />
  </div>
  
  <div class="keyboard">
    <Letter v-for="char in alphabet" :key="char" :char="char" />
  </div>

</template>

<style scoped>
.placeholder {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 120px;
}
.keyboard {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>