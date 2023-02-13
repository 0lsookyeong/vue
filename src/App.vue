<template>
  <div id="app">
    <todoHeader></todoHeader>
    <todoInput v-on:addTodo="addTodo"></todoInput>
    <todoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></todoList>
    <todoFooter v-on:removeAll="clearAll"></todoFooter>
  </div>
</template>

<script>

  import todoHeader  from './components/todoHeader.vue'
  import todoInput  from './components/todoInput.vue'
  import todoList  from './components/todoList.vue'
  import todoFooter  from './components/todoFooter.vue'

export default {
  data() {
    return {
      todoItems : []
    }
  },
  methods : {
    addTodo(todoItem){
      //로컬 스토리지에 데이터 추가하는 로직 
      localStorage.setItem(todoItem,todoItem);
      this.todoItems.push(todoItem);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems=[];
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index,1); 
      
    }
  },
  created(){ //beforeMount , mounted 등 라이프 사이클에 진행해도 결과 동일하나 추후 코드 구조 개선하고 나면 화면 렌더링에 문제가 생김 
    var len = localStorage.length ;
    if( len > 0){
      for( var i=0 ; i< len ; i++){
        this.todoItems.push(localStorage.key(i));


      }
    }
  },
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
