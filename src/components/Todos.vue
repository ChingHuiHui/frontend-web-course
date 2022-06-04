<template>
  <div class="space-y-3">
    <div
      v-for="todo in normalizedTodos"
      :key="todo.id"
      class="flex items-center space-x-2 p-3 rounded"
      :class="todo.completed ? 'bg-green-500' : 'bg-red-300'"
    >
      <span>{{ todo.user }}</span>
      <span>{{ todo.title }}</span>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref, computed } from 'vue'

const todos = ref([])
const users = ref([])

onMounted(async () => {
  const [todoData, userData] = await Promise.all([
    fetch('https://jsonplaceholder.typicode.com/todos').then((response) =>
      response.json()
    ),
    fetch('https://jsonplaceholder.typicode.com/users').then((response) =>
      response.json()
    ),
  ])

  todos.value = todoData.slice(0, 10)
  users.value = userData
})

const normalizedTodos = computed(() => {
  return todos.value.map(({ userId, ...rest }) => {
    const { name } = users.value.find(({ id }) => id === userId)

    return {
      ...rest,
      user: name,
    }
  })
})
</script>
