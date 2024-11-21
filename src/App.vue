<template>
  <div id="app">
    <!-- Navigation -->
    <ul>
      <li v-for="(page, index) in pages" :key="index" @click="changePage(page)" style="cursor: pointer;">
        {{ page }}
      </li>
    </ul>

    <!-- Main content -->
    <hr>

    <div>
      <PageHome v-if="activePage == 'home'"/>
      <PageArtists v-if="activePage == 'artists'"/>
      <PageRanking v-if="activePage == 'ranking'" />
      <PageVoting v-if="activePage == 'voting'" v-on:cp="changePage"/>
    </div>
  </div>
</template>

<script>
  import PageArtists from './components/PageArtists.vue';
  import PageHome from './components/PageHome.vue';
  import PageRanking from './components/PageRanking.vue';
  import PageVoting from './components/PageVoting.vue';

  /* eslint-disable */
  export default {
    name: 'App',
    components: {
      PageArtists,
      PageHome,
      PageRanking,
      PageVoting
    },
    data() {
      return {
        activePage: 'voting',
        pages: ['home', 'artists', 'ranking', 'voting']
      }
    },
    methods: {
      changePage(page) {
        console.log("Changing page to: " + page);
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
