<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>

    <router-view />
  </div>
</template>

<script>
import Skills from './components/Skills.vue'

export default {
  name: 'app',
  components: {
    Skills
  }
}
</script>

<style>
body {
  background: #eee;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 50%
}
nav {
  text-align: left;
  padding: 20px 20px 20px 0;
  margin-bottom: 30px
}
nav a {
  padding: 10px;
  text-decoration: none;
  background: #fff;
  color: rgb(0,110,255);
  border-radius: 3px;
  margin-right: 15px;
  font-weight: bold;
}
</style>
