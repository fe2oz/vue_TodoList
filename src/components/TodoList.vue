<template>
  <section>
    <ul>
      <li v-for="(todoItem, index) in propsdata" :key="todoItem">
        {{ todoItem }}
        <span @click="removeTodo(todoItem, index)">
          <i class="fa-solid fa-delete-left"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>

export default {

  methods: {
    removeTodo(todoItem, index){
      this.$emit('removeTodo', todoItem, index)
    }
  },
  props: ['propsdata']
}
</script>

<style>
  ul{
    list-style-type: none;
    margin:0; padding:0;
    margin-top: 10px;
    display: flex; justify-content: center; flex-flow: column; align-items: center;
  }
  li{
    width: 30em;
    height: 50px; min-height: 50px;
    display: flex; justify-content: space-between;
    line-height: 50px;
    background-color: pink;
    margin-bottom: 5px; margin-top: 5px;
    padding: 0.3rem;
    border-radius: 5px;
  }
  span{
    cursor: pointer;
    color: rgb(207, 50, 76);
  }

</style>
