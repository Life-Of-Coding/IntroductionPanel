<template>
  <IntroductionPanel></IntroductionPanel>
</template>

<script>
import IntroductionPanel from "./components/IntroductionPanel"

export default {
  name: 'App',
  components: {
    IntroductionPanel
  }
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
</style>
