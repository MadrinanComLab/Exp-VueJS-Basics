<template>
  <!--/ <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> /-->
  <h1>{{ title }}</h1><br>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {
    return {
      title: "My First Vue App :3"
    }
  },

  methods: {
    handleClick() {
      // NOTE: 'name' IN this.$refs.name WAS THE ref VALUE WE ASSIGNED IN THE INPUT TAG
      console.log(this.$refs.name.value)
      this.$refs.name.classList.add("active")
      this.$refs.name.focus()
      this.title = this.$refs.name.value
    }
  }
  /* components: {
    HelloWorld
  } */
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #DDD;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
