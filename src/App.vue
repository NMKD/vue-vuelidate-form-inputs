<template>
  <div id="app">
    <FormInput/>
  </div>
</template>

<script>
import FormInput from './components/Form.vue'

export default {
  name: 'App',
  components: {
    FormInput
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
