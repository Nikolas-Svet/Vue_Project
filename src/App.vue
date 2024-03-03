<!-- Второй файл -->
<template>
  <HelloWorld msg="Приветствую, пользователь!"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    handleClick() {
      alert('Button clicked in HelloWorld component!');
    }
  }
}
</script>

<style>
body {
  background-color: #808080;
}
#app {
  background-color: #808080;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


</style>
