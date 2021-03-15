<template>
  <div>
    <h1>To-do App</h1>
    <Todo />
  </div>
</template>

<script>
  import TodoApp from './components/TodoApp.vue'

  export default{
    components: {
      Todo: TodoApp
    }
  }
</script>

<style>
body{
  background-color: #F5EDFE;
  font-family: verdana;
}
h1 {
  font-size: 28px;
  text-align: center;
  padding: 18px;
}

</style>