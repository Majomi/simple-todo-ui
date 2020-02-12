<template>
  <div class="bg-red-300 text-gray-700">
    <slot name="title"></slot>
    <br />
    <slot name="message">Something is missing</slot>
    <button @click="onDelete">Delete</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  props: ['id'],
  methods: {
    async onDelete() {
      const response = await axios.delete(
        `http://localhost:3000/todo/${this.id}`
      )

      console.log(response)
    }
  }
}
</script>

<style scoped></style>
