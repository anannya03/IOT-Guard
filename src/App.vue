<template>
  <div class="section is-vcentered">
    <Header />
    <div class="container">
      <line-chart />
    </div>
    <Footer />
  </div>
</template>

<script>
import "./../node_modules/bulma/css/bulma.css";
import Header from "./components/Header.vue";
import LineChart from "./components/LineChart.vue";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    LineChart,
    Header,
    Footer,
  },
};
</script>

<style>
.section {
  min-height: 100vh !important;
  background-color: #faf6e9;
}
</style>
