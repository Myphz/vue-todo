<template>
  <button :style="cssVars">{{title}}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    title: String,
    color: String,
  },

  computed: {
    cssVars () {
      return {
        '--color': this.color,
      }
    }
  }
}
</script>

<style scoped>
  button {
    opacity: .7;
    text-align: center;
    background-color: var(--color);
    border-radius: .25rem;    
    border: none;
    color: #fff;
    font-family: system-ui,-apple-system,system-ui,"Helvetica Neue",Helvetica,Arial,sans-serif;
    padding: .8rem 1.5rem;
    transition: all 250ms;
    user-select: none;
    -webkit-user-select: none;
  }

  button:hover,
  button:focus {
    opacity: .9;
  }

  button:hover {
    transform: translateY(-1px);
  }

  button:active {
    opacity: 1;
    transform: translateY(0);
  }
</style>