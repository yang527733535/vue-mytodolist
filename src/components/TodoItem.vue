<template>

 <li  :style="{background:bgColor}" @mouseenter='handleenter(true)'  @mouseleave='handleenter(false)' >
          <label>
            
            <input v-model="todo.complete" type="checkbox"/>
            <span>{{todo.title}}</span>
          </label>
          <button class="btn btn-danger" @click='deleitem' v-if="isShow" >删除</button>
        </li>
</template>

<script>
export default {
  props:['index','todo','deletetodo'],
  data(){
   return {
     bgColor:"white", //默认的背景颜色 
     isShow:false  //表示按钮默认是否显示
   }
  },
  methods:{
    handleenter(isenter){
      console.log('as');
      if(isenter){
          this.bgColor = 'gray'
          this.isShow = true
      }else{
         this.bgColor = 'white'
         this.isShow = false
      }
    },
    deleitem(){
      const {todo,index,deletetodo} = this //这里是解构赋值呀 
      if(window.confirm(`确认删除${todo.title}吗？`)){
          deletetodo(index)
      }
    }
  }
}
</script>

<style scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
.btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }
  
  .btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }
  
  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }
  
  .btn:focus {
    outline: none;
  }
</style>
