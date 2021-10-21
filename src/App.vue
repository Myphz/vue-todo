<template>
  <div class="container">
    <Header title="Vue BEST TODO App"/>
    <TaskForm v-show="showAddTask" @add-task="addTask"/>
    <div class="buttons">
      <Button @click.native="toggleAdd" :title="addText" :color="addColor"/>
      <Button @click.native="onRemoveClick()" :title="removeText" color="red"/>
    </div>

    <Tasks @delete-task="deleteTask" :watcher="deleteMode" :tasks="tasks" />

  </div>
</template>

<script>
import Header from "./components/Header";
import Button from "./components/Button";
import Tasks from "./components/Tasks";
import TaskForm from "./components/TaskForm";

export default {
  name: 'App',
  components: {
    Header,
    Button,
    Tasks,
    TaskForm,
  },

  data() {
    return {
      tasks: [],
      deleteMode: false,
      removeText: "Remove",
      addText: "Add",
      addColor: "darkgreen",
      showAddTask: false,
    }
  },

  created() {
    this.tasks = [
      {
        id: 0,
        title: "Test task #1",
        description: "First task description",
        time: "Tomorrow",
      },
      {
        id: 1,
        title: "Test task #2",
        description: "Second task description",
        time: "Saturday",
      },
    ]
  },

  methods: {
    onRemoveClick() {
      this.deleteMode = !this.deleteMode;
      this.removeText = ["Remove", "Cancel"][this.deleteMode | 0];
    },

    addTask(task) {
      task.id = this.tasks[this.tasks.length - 1];
      this.tasks.push(task);
    },

    toggleAdd() {
      this.showAddTask = !this.showAddTask; 
      this.addText = ['Add', 'Close'][this.showAddTask | 0];
      this.addColor = ["darkgreen", "darkred"][this.showAddTask | 0];
    },

    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
  }
}
</script>

<style scoped>
  .container {
    max-width: 500px;
    margin: 10px auto;
    overflow: auto;
    padding: .5em;
    width: 25vw;
    border: 1px solid darkorange;
    border-radius: 5px;
  }

  .buttons {
    display: flex;
    justify-content: center;
  }
</style>
