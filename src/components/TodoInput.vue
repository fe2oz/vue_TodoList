<template>
  <div class="input">
    <input type="text" v-model="newTodoItem"
    placeholder="할 일을 입력해 보세요!" v-on:keyup.enter="addTodo">
    <span type="button" class="addBtn" @click="addTodo">
      <i class="fa-solid fa-plus plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data(){
    return{
      newTodoItem : ""
    }
  },
  methods: {
    addTodo(){
      if(this.newTodoItem !== ""){
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo', value);
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodoItem = ""
    }
  }
}
</script>

<style>
  .plus{
    color: #000;
  }
  .input{
    display: flex; justify-content: center; align-items: center;
  }
  input{
    width: 30em; height: 50px;
    border: 0; border-radius: 5px;
    background-color: pink;
    padding: 0 0.5rem;
  }
  input:focus{
    outline: none;
  }
  .addBtn{
    width: 3em; height: 50px;
    background-color: pink;
    border-radius: 5px;
    text-align: center;
    vertical-align: middle;
    line-height: 50px;
    color: white;
    cursor: pointer;
    margin-left: 5px;
    padding-right: 5px;
}
</style>

