<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/Header';
export default {
  components: { Header }
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  background-color: #282c34;
  margin: 0;
  padding: 50px;
  height: calc(100vh - 100px);
}
button {
  color: #444;
  background-color: #f3f3f3;
  padding: 5px 10px;
  border-radius: 3px;
  font-weight: bold;
  font-size: 1.2rem;
  outline: none;
  margin: 3px;
}
input, textarea {
  width: 100%;
  padding: 10px;
  margin: 8px 0;
  font-size: 1.2rem;
}
label {
  float: left;
  font-size: 1.2rem;
  color: orange;
}

</style>
