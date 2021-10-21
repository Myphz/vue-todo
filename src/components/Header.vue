<template>
  <div>
    <h1>{{title}}</h1>
  </div>
</template>

<script>

export default {
  name: "Header",
  props: {
    title: String,
  },
}
</script>

<style scoped>
  h1 {
    text-align: center;
    color: rgb(31, 30, 30);
    font-family: Arial, Helvetica, sans-serif;
  }
</style>
