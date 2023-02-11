<template>
  <div id="app">
    <todoHeader></todoHeader>
    <todoInput></todoInput>
    <todoList></todoList>
    <todoFooter></todoFooter>
  </div>
</template>

<script>

  import todoHeader  from './components/todoHeader.vue'
  import todoInput  from './components/todoInput.vue'
  import todoList  from './components/todoList.vue'
  import todoFooter  from './components/todoFooter.vue'

export default {
  components: {
    'todoHeader': todoHeader,
    'todoInput': todoInput,
    'todoList': todoList,
    'todoFooter': todoFooter
  }
}
</script>

<style>
   body {
    text-align: center;
    background-color: #F6F6F8;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
  }           
</style>
