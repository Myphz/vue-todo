<template>
  <div>
    <div v-for="task in tasks" :key="task.id">
      <Task @delete-task="$emit('delete-task', task.id)" :watcher="watcher" :task="task"/>
    </div>
  </div>
</template>

<script>
import Task from "./Task.vue"

export default {
  name: "Tasks",
  components: {
    Task
  },
  
  props: {
    tasks: Array,
    watcher: Boolean,
  },
}
</script>