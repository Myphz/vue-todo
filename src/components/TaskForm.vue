<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Title</label>
      <input type="text" v-model="title" name="text" placeholder="Task Title" />
    </div>

    <div class="form-control">
      <label>Description</label>
      <input type="text" v-model="description" name="text" placeholder="Description" />
    </div>

    <div class="form-control">
      <label>Time</label>
      <input
        type="text"
        v-model="time"
        name="day"
        placeholder="Time"
      />
    </div>

    <input type="submit" value="Save Task" class="btn" />
  </form>
</template>

<script>
export default {
  name: "TaskForm",

  data() {
    return {
      title: "",
      description: "",
      time: "",
    }
  },

  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.title) return alert("Please insert title.");
      this.$emit("add-task", {
        title: this.title,
        description: this.description,
        time: this.time,
      });

      this.title = "";
      this.description = "";
      this.time = "";
    }
  }

}
</script>

<style scoped>

  * {
    font-family: Arial, Helvetica, sans-serif;
  }

  .add-form {
    margin-bottom: 40px;
    text-align: center;
  }

  .form-control label {
    display: block;
  }

  .form-control input {
    width: 90%;
    height: 40px;
    margin: 15px;
    padding: 3px 7px;
    font-size: 17px;
  }

  .btn {
    float: none;
    opacity: .85;
    color: white;
    text-align: center;
    align-items: center;
    background-clip: padding-box;
    background-color: black;
    border: 1px solid transparent;
    border-radius: .25rem;
    box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
    box-sizing: border-box;
    color: #fff;
    cursor: pointer;
    font-family: system-ui,-apple-system,system-ui,"Helvetica Neue",Helvetica,Arial,sans-serif;
    font-size: 16px;
    font-weight: 600;
    line-height: 1.25;
    margin: 5px;
    min-height: 3rem;
    padding: calc(.875rem - 1px) calc(1.5rem - 1px);
    position: relative;
    text-decoration: none;
    transition: all 250ms;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
    vertical-align: baseline;
    width: auto;
  }

  .btn:hover,
  .btn:focus {
    opacity: .9;
    box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
  }

  .btn:hover {
    transform: translateY(-1px);
  }

  .btn:active {
    opacity: 1;
    box-shadow: rgba(0, 0, 0, .06) 0 2px 4px;
    transform: translateY(0);
  }
</style>