<template>
  <div>
    <CreateTodo />
    <TodoList />
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from '@/components/TodoList'
import CreateTodo from '@/components/CreateTodo'
export default {
  name: 'Home',
  components: {
    TodoList,
    CreateTodo
  }
}
</script>
