<template>
  <div class="max-w-sm mx-auto text-center">
    <Todo
      :to="{ name: 'SingleTodo', params: { id: todo.id } }"
      v-for="todo in state.todos"
      :key="todo.id"
      :id="todo.id"
    >
      <template #title>{{ todo.title }}</template>
      <template #message>{{ todo.message }}</template>
    </Todo>
  </div>
</template>

<script>
import axios from 'axios'
import Todo from '@/components/Todo'
import { reactive, onMounted } from '@vue/composition-api'
export default {
  components: {
    Todo
  },
  setup() {
    const state = reactive({
      todos: []
    })
    const fetchTodos = async () => {
      alert('')
      const response = await axios.get('http://localhost:3000/')
      state.todos = response.data
    }

    onMounted(async () => {
      await fetchTodos()
    })

    return {
      state,
      fetchTodos
    }
  }
}
</script>

<style scoped></style>
