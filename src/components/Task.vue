<template>
  <div>
    <h2>{{task.title}}
      <transition name="fade">
        <i @click="$emit('delete-task', task.id)" v-show="watcher" class="fas fa-times"></i>
      </transition>
    </h2>
    <h4>{{task.description}}</h4>
    <h5>On: {{task.time}}</h5>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
    watcher: Boolean,
  },
}
</script>

<style scoped>
  h2 {
    color: darkorange;
  }

  i {
    float: right;
    color: red;
    transition: all 0.25s;
  }

  i:hover {
    color: darkred;
  }

  div {
    line-height: 20%;
    font-family: system-ui,-apple-system,system-ui,"Helvetica Neue",Helvetica,Arial,sans-serif;
    margin: 15px;
    padding: 15px;
    background: #e6e6e6;
    border-radius: 5px;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .25s;
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
</style>