<template>
  <div id="app">
    <form @submit.prevent="getData">
      <div>
        <button>expand node with id O-111</button>
        <button>collapse node with id O-111</button>
        <button>add node as root's child</button>
        <button>`add node as first child's child</button>
        <button>remove node id="0-5"</button>
        <button>remove node id="0-6"</button>
      </div>

      <Chart :data="data"></Chart>
    </form>
  </div>
</template>

<script>
import Chart from "./components/Chart.vue";

export default {
  name: "app",
  data() {
    return {
      data: []
    };
  },
  components: {
    Chart
  },
  methods: {},
  created() {
    fetch(
      "https://gist.githubusercontent.com/bumbeishvili/dc0d47bc95ef359fdc75b63cd65edaf2/raw/c33a3a1ef4ba927e3e92b81600c8c6ada345c64b/orgChart.json"
    )
      .then(d => d.json())
      .then(d => {
        console.log("fetched data");
        this.data = d;
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
