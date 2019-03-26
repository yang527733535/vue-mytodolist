<template>
 <ul class="todo-main">
   <TodoItem  :selectAlltodos = 'selectAlltodos' 
   :deleteCompletetodos='deleteCompletetodos' 
   :deletetodo='deletetodo' 
   :todo="todo"  
   :index='index' 
   :key="index"
   v-for="(todo,index) in todos">
   </TodoItem>
       
      </ul>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  components:{
    TodoItem
  },
   props:['todos','deletetodo','selectAlltodos','deleteCompletetodos' ],
  data(){
   return {

   }
  }
}
</script>

<style scoped>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
/*item*/

</style>
