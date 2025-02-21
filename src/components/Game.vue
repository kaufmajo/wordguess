<script setup>
import { ref, watch } from 'vue'
import Letter from './Letter.vue'
import Blank from './Blank.vue'

const alphabet = Array.from({ length: 26 }, (_, i) => String.fromCharCode(97 + i));
const input = ref('hello');
const word = Array.from(input.value);
let guesses = ref(Array.from({ length: word.length }, () => ''));
const maxGuesses = 6;

watch(input, (newVal) => {
  guesses = Array.from(Array.from({ length: newVal.length }, () => ''));
});

function handleGuess(char) {
  word.map((letter, index) => {
    if (letter === char) {
      guesses.value[index] = char;
    }
  })

  if (guesses.value.join('') === word.join('')) {
    alert('You win!');
  }
};

</script>

<template>

  <h1>Hangman</h1>

  <input type="text" v-model="input" />

  <div>

  <div class="blank">
    <Blank v-for="char in guesses" :key="char" :char="char" />
  </div>

  <div class="keyboard">
    <Letter v-for="char in alphabet" :key="char" :char="char" @guess="handleGuess" />
  </div>

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