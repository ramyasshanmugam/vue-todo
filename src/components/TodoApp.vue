<template>
  <div id="app">
    <div class="container">
        <div class="todo-app">
          <h2>ToDo List</h2>
          <div class="row">
            <input type="text" placeholder="Add a new Task" class="input" v-model="newTask">
            <AddButton @addTask="addTasks" />

            <!-- <button class="btn_add" @click="addTasks">Add Task</button> -->
          </div>
            <TodoTable :tasks="tasks" @toggle-status="handleClick"  @delete-status="deleteTask"/>
            

        </div>
      </div>
    </div>
</template>

<script >
import TodoTable from '@/components/TodoTable.vue';
import AddButton from '@/components/AddButton.vue';
 export default{
    name: 'App',
    components:{
      TodoTable,AddButton
    },
    data(){
      return{
        tasks:[],
        newTask:'',
        taskId:1
      }
    },
    methods:{
         handleClick(todo) {
      todo.status = todo.status === 'completed' ? 'pending' : 'completed';
    },
        addTasks() {
            console.log(this.tasks);
            this.tasks.push({
              id:this.taskId++,
              title: this.newTask,
              status:'pending'
            })
            this.newTask = ''
    },
    deleteTask(index){
          this.tasks.splice(index, 1);
          console.log('this',this.tasks)
        },
  }
}
</script>

<style scoped>
.container{
    width:100%;
    min-height: 100vh;
    background: rgb(245, 240, 255);
    padding: 10px;
}

.container .todo-app{
    width:100%;
    max-width: 540px;
    background-color: #fff; 
    margin:100px auto 20px;
    padding:40px 30px 70px;
    border-radius: 10px;
}

.todo-app h2{
    display: flex;
    align-items: center;
    color: #002765;
    justify-content: center;
}

.row{
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 30px;
    padding-left:20px ;
    background: #edeef0;
}

.row .input{
    flex: 1;
    border:none;
    outline: none;
    background-color: transparent;
    padding: 10px;
    font-size: 14px;
}

.todo-items{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 5px;
}

</style>


