<template>
  <div id="app">
    <header>
      <img src="./assets/logo.png">
    </header>
    <router-view/>

    <footer>
      <p>Copyright 2019</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header img {
  max-height: 100px;
}

header,
footer {
  max-height: 100px;
  background-color: rgb(116, 223, 255);
}
</style>
