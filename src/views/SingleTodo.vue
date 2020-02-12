<template>
  <Todo :id="todo.id">
    <template #title>{{ todo.title }}</template>
    <template #message>{{ todo.message }}</template>
  </Todo>
</template>

<script>
import axios from 'axios'
import { onMounted, ref } from '@vue/composition-api'
import Todo from '@/components/Todo'
export default {
  components: {
    Todo
  },
  setup(props, ctx) {
    let todo = ref({})

    onMounted(async () => {
      const id = ctx.root.$route.params.id
      try {
        const { data } = await axios.get(`http://localhost:3000/todo/${id}`)
        todo.value = data
      } catch (err) {
        alert(err)
      }
    })
    return {
      todo
    }
  }
}
</script>

<style scoped></style>
