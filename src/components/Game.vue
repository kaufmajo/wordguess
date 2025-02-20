<script setup>
import { ref, watch } from 'vue'
import Letter from './Letter.vue'
import Blank from './Blank.vue'

const alphabet = Array.from({ length: 26 }, (_, i) => String.fromCharCode(97 + i));
const word = ref(Array.from('hello'));
const guesses = ref(Array.from({ length: word.value.length }, () => ''));
const maxGuesses = 6;

function handleGuess(char) {
  word.value.map((letter, index) => {
    if (letter === char) {
      guesses.value[index] = char;
    }
  })

  if (guesses.value.join('') === word.value.join('')) {
    alert('You win!');
  }
};

</script>

<template>

  <div class="blank">
    <Blank v-for="char in guesses" :key="char" :char="char" />
  </div>

  <div class="keyboard">
    <Letter v-for="char in alphabet" :key="char" :char="char" @guess="handleGuess" />
  </div>

</template>

<style scoped>
.blank {
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