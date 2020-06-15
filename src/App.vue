<template>
  <div id="app">
    <navbar />
   <skills />
  </div>
</template>

<script>
import navbar from './components/Navbar.vue'
import skills from './components/Skills.vue'

export default {
  name: 'app',
  components: {
    navbar, skills,
  }
}
</script>

<style>
body {
  background-color: #EEEEEE;
  font-family: 'Montserrat', sans-serif;

}
body, html {
  margin: 0;
  height: 100%;
}

</style>
