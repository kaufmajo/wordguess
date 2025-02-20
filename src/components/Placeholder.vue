<script setup>
defineProps({
  char: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <div class="letter">
    {{ char }}
  </div>
</template>

<style scoped>
.letter {
  display: inline-block;
  width: 4rem;
  height: 4rem;
  border: 1px solid #333;
  text-align: center;
  line-height: 2rem;
  font-size: 1.25rem;
}
</style>
