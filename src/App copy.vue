<template>
  <div id="app">
    <Header />
    <Movies />
  </div>
</template>

<script>
import Header from './components/Header';
import Movies from './components/Movies';

export default {
  name: 'App',
  components: {
    Header,
    Movies
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
