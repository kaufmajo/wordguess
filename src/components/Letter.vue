<script setup>
defineProps({
  char: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div class="letter" @click="$emit('guess', char)">
    {{ char }}
  </div>
</template>

<style scoped>
.letter {
  width: 4rem;
  height: 4rem;
  border: 1px solid #333;
  text-align: center;
  line-height: 2rem;
  font-size: 1.25rem;
}
.letter:hover {
  background-color: #f0f0f0;
  cursor: pointer;
}
</style>
