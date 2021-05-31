<template>
  <div id="app">
  <TodoHeader v-on:search="searchmethod"></TodoHeader>
  <TodoInput v-on:addTodo="addTodo"></TodoInput>
  <TodoList v-bind:propsdata="todoItems" v-bind:searchKeyword="searchKeyword" @removeTodo="removeTodo"></TodoList>
  <TodoFooter v-on:removeAll="clearAll" v-on:check="check"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';
export default {
  data(){
  return{
    todoItems : [],
    searchKeyword :String,
  }
},
 created(){
        if(localStorage.length > 0){
            for(var i=0; i<localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        };
        
    },
methods : {
  searchmethod(searchKeyword){
    console.log("검색기능넣기~"+searchKeyword);
    this.searchKeyword=searchKeyword;
  },
  addTodo(todoItem){
    localStorage.setItem(todoItem, todoItem);
    this.todoItems.push(todoItem);
  },
  clearAll(){
    localStorage.clear();
    this.todoItems=[];
  },
  removeTodo(todoItem, index){
    localStorage.removeItem(todoItem);
    this.todoItems.splice(index, 1);
  },
  check(){
    console.log("props check하기!!");
    this.todoItems.push('props체크 중입니당');
  }
},
  components : {
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  }
}
</script>

<style>

body{
        text-align: center;
        background-color: #f6f6f8;
    }
input{
        border-style:groove;
        width: 200 px;
    }
    button {
        border-style : groove;
    }
    .shadow {
        box-shadow : 5px 10px 10px rgba(0, 0, 0, 0.03)
    }

</style>
