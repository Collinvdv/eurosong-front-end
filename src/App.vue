<template>
  <div id="app">
    <!-- Navigation -->
    <ul>
      <li v-for="(page, index) in pages" :key="index" @click="changePage(page)">
        {{ page }}
      </li>
    </ul>

    <!-- Main content -->
    <hr>

    <div>
      <PageHome />
      <PageRanking />
      <PageVoting />
    </div>
  </div>
</template>

<script>
  import PageHome from './components/PageHome.vue';
  import PageRanking from './components/PageRanking.vue';
  import PageVoting from './components/PageVoting.vue';

  /* eslint-disable */
  export default {
    name: 'App',
    components: {
      PageHome,
      PageRanking,
      PageVoting
    },
    data() {
      return {
        activePage: 'home',
        pages: ['home', 'ranking', 'voting']
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
