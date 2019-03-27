<template>
 <div class="todo-container">
    <div class="todo-wrap">
      <TodoHeader :addTodo='addTodo'></TodoHeader>
       <TodoList :deletetodo='deletetodo' :todos='todos'></TodoList> 
       <TodoFooter :selectAlltodos='selectAlltodos' :deleteCompletetodos='deleteCompletetodos' :todos='todos'></TodoFooter>
    </div>
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {

 components:{
     TodoHeader,
     TodoList,
     TodoFooter,
    
 },
  data(){
   return {
     //从localstorage读取todos
       todos: JSON.parse( window.localStorage.getItem('todos_key')||'[]')
      
   }
  },
  watch:{  //深度监视
    todos:{
      deep:true,
      handler:function (value) {
        //将todos最新的值的json数据，保存到localstorage
        window.localStorage.setItem('todos_key',JSON.stringify(value))
      }
    }
  },
  methods:{
    addTodo(todo){
        this.todos.unshift(todo)
    },
    deletetodo(index){
      this.todos.splice(index,1)
    },
    //删除所有选中todo 
  deleteCompletetodos(){

  this.todos= this.todos.filter(todo=>!todo.complete)
   
    },
    //全选或全部选 
    selectAlltodos(check){
      this.todos.forEach(todo=>{
          todo.complete = check
      })
    }
  }
}
</script>

<style scoped>
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

</style>
