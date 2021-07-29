<template>
  <div id="app">
    <div class="card">
      <div class="card-title">
        <h1>Random Gif Cat</h1>
      </div>
      <gifcats></gifcats>
    </div>
  </div>
</template>

<script>

import Cats from './components/Cats.vue'
export default {
  name: 'App',
  components: {
    'gifcats': Cats,
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

.card {
  margin: 0 400px;
}

.card-title {
  margin: 0;
  padding: 10px;
  text-align: center;
  background: #54436B;
  color: #ACFFAD; 
}
</style>
