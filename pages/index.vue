
<script setup>
const todos = ref([])

const todoData = await useFetch(() => 'http://localhost:1337/api/todos/')
try {
  console.log(todoData.data.value.data)
  todoData.data.value.data.forEach(data => console.log(data))
  todos.value = todoData.data.value.data
} catch (error) {
  console.log(error)
}

</script>


<template>
  <div>
    <ul>
      <li v-for="(todo,index) in todos">{{todo.todoname}}</li>
    </ul>
  </div>
</template>