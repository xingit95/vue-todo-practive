<template>
  <div class="list-todos">
    <a @click="goList(item.id)" class="list-todo activeListClass list" :class="{'active':item.id===todoId}" v-for="item in items" :key="item.count">
      <span class="icon-lock" v-if="item.locked"></span>
      <span class="count-list" v-if="item.count>0">{{item.count}}</span>
      {{item.title}}
    </a>
    <a href="" class="link-list-new">
      <span class="icon-plus"></span>
      新增
    </a>
  </div>
</template>
<script>
import { getTodoList, addTodo } from "../api/api";
export default {
  data() {
    return {
      // items:[
      //   {title:'星期一',count:1,locked:true},
      //   {title:'星期二',count:2,locked:true},
      //   {title:'星期三',count:3,locked:false},
      // ]
      items: [],
      todoId: ''
    };
  },
  created(){
    // console.log(this);
    getTodoList({}).then(res=>{
      const TODOS=res.data.todos;
      this.items=TODOS;
      this.todoId=TODOS[0].id;
    });
  },
  methods:{
    goList(id){
      this.todoId=id;
    },
    addTodoList(){
      addTodo({}).then(data=>{
        getTodoList({}).then(res=>{
          const TODOS= res.data.todos;
          this
        });
      });
    }
  }
};
</script>
<style lang="less">
@import "../common/style/menu.less";
// @import "../common/style/layouts.less";
</style>

