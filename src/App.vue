<template>
  <div id="app">
    <!-- Navigation -->
    <ul>
      <li @click="changePage('home')">
        Home
      </li>
      <li @click="changePage('ranking')">
        Ranking
      </li>
      <li @click="changePage('voting')">
        Voting
      </li>
    </ul>

    <!-- Main content -->
    <hr>

    <div>
      {{ activePage }}
    </div>
  </div>
</template>

<script>
  /* eslint-disable */
  export default {
    name: 'App',
    data() {
      return {
        activePage: 'home'
      }
    },
    methods: {
      changePage(page) {
        this.activePage = page;
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
