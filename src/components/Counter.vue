<template>
  <div class="flex space-x-5">
    <button @click="decrease">Decrease</button>
    <h2 class="text-3xl">COUNT: {{ count }}</h2>
    <button @click="increase">Increase</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)

const decrease = () => {
  count.value--
}

const increase = () => {
  count.value++
}
</script>
