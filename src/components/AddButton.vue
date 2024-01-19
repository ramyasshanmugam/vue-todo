<template>
    <button class="btn_add" @click="addTasks">Add Task</button>
</template>

<script>
export default{
 methods: {
   addTasks() {
      this.$emit('addTask');
    },
 }
}
</script>

<style scoped>
.btn_add{
 border: none;
    outline: none;
    padding: 12px 20px;
    background: blue;
    color: #fff;
    font-size: 14px;
    cursor: pointer;
    border-radius: 10px;
    
}
</style>
