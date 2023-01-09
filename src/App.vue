<template>
  <div id="app">
    <FormLogin/>
  </div>
</template>

<script>
import FormLogin from './components/Form.vue'
export default {
  name: 'App',
  components: {
    FormLogin
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}
</style>
