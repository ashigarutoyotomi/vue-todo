<template>
<div>
  <p v-if="todoList.length >0">
    todo els
    <ul>
      <li v-for="item in todoList">{{item}}</li>
      </ul>
    </p>
    
    <p v-else>no items</p>
    <input v-model="field" type="text">
    <button @click="add"> add</button>
    <button @click="remove"> delete</button></div>
</template>

<script>
export default {
  data(){
    return {todoList:[],
    field:""};
  },
  mounted(){
    if(localStorage.getItem('todoList')==undefined){
      this.todoList =[]
    }else{
      this.todoList = JSON.parse(localStorage.getItem('todoList'))
    }
  },
  methods:{
    add:function (event){
      this.todoList.push(this.field)
      localStorage.setItem('todoList',JSON.encode(this.todoList))
      this.field=null
    },
    remove :function(){
      this.todoList.pop()
    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
