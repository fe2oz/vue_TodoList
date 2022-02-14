<template>
  <div class="footer">
    Clear All
    <span class="removeBtn" @click="clearTodo">
      <i class="fa-solid fa-trash"></i>
    </span>
  </div>
</template>

<script>

export default {
  methods: {
    clearTodo(){
      this.$emit('removeAll')
    }
  }
}
</script>


<style scoped>
  .footer{
    width: 10em; height: 2.5em;
    background: pink;
    display: flex; align-items: center; justify-content: center;
    border-radius: 5px;
    margin: 0 auto; margin-top: 10px;
  }
  .removeBtn{
    padding-left: 3px;
    color: rgb(207, 50, 76);
  }
</style>
