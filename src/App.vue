<template>
  <div id="app">
    <div v-for="(grade, index) in grades" :key="index">
      <CounterComponent :initialValue="grade"/>
    </div>
  </div>
</template>

<script>
import CounterComponent from './components/CounterComponent.vue'

export default {
  name: 'App',
  components: {
    CounterComponent
  },
  data() {
    return {
      grades: [10, 12, 13, 14, 15]
    }
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
