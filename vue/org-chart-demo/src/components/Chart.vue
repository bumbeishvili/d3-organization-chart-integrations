<template>
  <div  ref="svgElementContainer" >

  </div>
</template>

<script>
import * as TreeChart from "d3-org-chart";

export default {
  name: "Chart",
  props: ["data"],
  data() {
    return {
      chartReference: null
    };
  },
  watch: {
    data(value) {
      console.log("got new data", value);
      this.renderChart(value);
    }
  },
  created() {
    console.log(this.TreeChart);
  },
  methods: {
    renderChart(data) {
      console.log("rendering graph",this.$refs.svgElementContainer);
      if (!this.chartReference) {
        this.chartReference = new TreeChart();
      }
      this.chartReference
        .container(this.$refs.svgElementContainer) // node or css selector
        .data(data)
        .svgWidth(500)
        .initialZoom(0.4)
        .onNodeClick(d => console.log(d + " node clicked"))
        .render();

      console.log(data);
    }
  }
};
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
