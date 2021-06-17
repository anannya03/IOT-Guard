<template>
  <div class="section is-vcentered">
    <Header />
    <div class="container graph-container has-text-centered mt-5">
      <LineChart />
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
.graph-container {
  max-width: 60rem !important;
}
</style>
