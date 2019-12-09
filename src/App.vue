<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <PeopleList :height=height />
  </div>
</template>

<script>
import PeopleList from '@/components/PeopleList.vue'

export default {
  name: 'app',
  components: {
    PeopleList
  },
  data() {
    return {
      height : 170
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
