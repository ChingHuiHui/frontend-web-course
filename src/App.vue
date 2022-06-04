<template>
  <main class="min-h-screen flex flex-col">
    <Header />
    <div class="container mx-auto flex-1 my-10">
      <Counter class="mb-5" />
      <hr />
      <Todos />
    </div>
    <Footer />
  </main>
</template>

<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

import Counter from './components/Counter.vue'
import Todos from './components/Todos.vue'
</script>
