<template>
  <form class="flex flex-col bg-gray-400 max-w-sm mx-auto" @submit.prevent="createTodo">
    <label for="title">Title</label>
    <input v-model="todo.title" type="text" name="title" id="title" />

    <label for="message">Message</label>
    <textarea v-model="todo.message" type="text" name="message" id="message" />
    <button type="submit">Submit</button>
  </form>
</template>

<script>
import axios from 'axios'
import { ref } from '@vue/composition-api'
export default {
  setup() {
    const todo = ref({
      title: '',
      message: ''
    })
    const createTodo = async () => {
      await axios.post('http://localhost:3000/todo', todo.value)
      todo.value.title = ''
      todo.value.message = ''
    }
    return {
      createTodo,
      todo
    }
  }
}
</script>

<style scoped></style>
