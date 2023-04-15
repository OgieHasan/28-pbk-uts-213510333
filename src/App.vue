<template>
  <div class="todo-list">
    <h1>To-Do List</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" type="text" placeholder="Enter task...">
      <button type="submit">Add</button>
    </form>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <input type="checkbox" v-model="task.completed" @change="updateTask(task)">
        <span :class="{ completed: task.completed }">{{ task.title }}</span>
        <button @click="deleteTask(task)">X</button>
      </li>
    </ul>
  </div>
  <footer>copyright-ogiehasan</footer>
</template>
<script>
export default {
  data() {
    return {
      tasks: [],
      newTask: "",
      taskId: 0
    };
  },
  methods: {
    addTask() {
      if (this.newTask === "") return;
      this.tasks.push({
        id: this.taskId++,
        title: this.newTask,
        completed: false
      });
      this.newTask = "";
    },
    updateTask(task) {
      task.completed = !task.completed;
    },
    deleteTask(task) {
      const index = this.tasks.indexOf(task);
      this.tasks.splice(index, 1);
    }
  }
};
</script>
<style>
*{
  background-color: aquamarine;
}
.todo-list {
  max-width: 500px;
  margin: 0 auto;
  padding: 40px;
  font-size: 1.2rem;
  background-color: blueviolet;
}

.todo-list h1 {
  text-align: center;
  color: azure;
  background-color: yellowgreen;
}

.todo-list form {
  display: flex;
  margin-bottom: 20px;
}

.todo-list input[type="text"] {
  flex: 1;
  padding: 8px;
  font-size: 1.2rem;
  background-color: yellowgreen;
}

.todo-list button[type="submit"] {
  margin-left: 10px;
  padding: 8px;
  font-size: 1.2rem;
  background-color: blue;
}

.todo-list ul {
  list-style: none;
  padding: 0;
}

.todo-list li {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.todo-list input[type="checkbox"] {
  margin-right: 10px;
}

.todo-list .completed {
  text-decoration: line-through;
  color: grey;
}

.todo-list button {
  margin-left: 10px;
  padding: 8px;
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 1.2rem;
  color: white;
}
footer{
  text-align: center;
  background-color: yellowgreen;
}
</style>
