<template>
  <div id="app">
    <Header/>
    <line-chart/>
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import LineChart from './components/LineChart.vue'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    LineChart,
    Header,
    Footer
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
  background-color: #FFEEDE;
  min-height: 100vh !important;
}
</style>
