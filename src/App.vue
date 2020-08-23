<template>
  <div id="app">
    <header>
      <router-link :to="{ name: 'HelloWorld' }">Home</router-link>
      <router-link to="/playlist">Playlist</router-link>
    </header>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  padding-top: 30px;
  padding-bottom: 30px;
  background-color: black;
  color: white;
  font-weight: bold;
  font-size: 40px;
}

a {
  color: inherit;
  text-decoration: none;
}

</style>
