<template>
     <table>
      <thead>
        <tr>
          <th>Task</th>
          <th>Status</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody >
        <tr v-for="(todo,index) in tasks" :key="index" >
            <td :class="{ 'txt_title': true,'completed-task': todo.status === 'completed' }">{{ todo.title }}</td>
            <td>
            <button :class="{ 'completed': todo.status === 'completed', 'pending': todo.status === 'pending' }" @click="handleClick(todo)">{{todo.status}}</button>
            </td>
            <td>
            <img src="@/assets/delete.png" @click="deleteTask(index)" class="delete_icon" alt="Delete" />
            </td>
        </tr>
      </tbody>
    </table>
</template>

<script>
export default {
  props: ['tasks'],
  methods: {
   handleClick(todo) {
      this.$emit('toggle-status', todo);
    },
   deleteTask(index) {
      this.$emit('delete-status', index);
    },
  }
};
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}
th{
    font-family: "Poppins";
    font-weight: bold;
    border: none;
  padding: 8px;
  text-align: center;
}
 td {
  border: none;
  padding: 8px;
  text-align: center;
}

.txt_title{
     font-size: 16px;
 font-family: "Poppins_M";
}

.delete_icon{
  width:20px;
  height: 20px;
  cursor: pointer;
}

.completed{
  color: green;
  border: none;
  outline: none;
  cursor: pointer;
  border-radius: 10px;
  background-color: #fff !important;
  font-size: 16px;
 font-family: "Poppins_M";
}

.pending{
  color: blue;
  border: none;
  outline: none;
  cursor: pointer;
  border-radius: 5px;
  background-color: #fff !important;
  font-size: 16px;
 font-family: "Poppins_M";
        
}

.completed-task {
  text-decoration: line-through;
   font-size: 16px;
 font-family: 'Poppins','sans-serif';
     font-weight:bold;

}


</style>
