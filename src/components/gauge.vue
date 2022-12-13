<template>
  <section class="charts">
    <vue-highcharts
      :options="options"
      ref="chart"
      :highcharts="Highcharts"
    ></vue-highcharts>
  </section>
</template>
<script>
import VueHighcharts from "./VueHighcharts.vue";
import More from "highcharts/highcharts-more";
import Highcharts from "highcharts";

More(Highcharts);
let timer = null;
const data = {
  chart: {
    type: "gauge",
    backgroundColor: "none",
    plotBackgroundColor: null,
    plotBackgroundImage: null,
    plotBorderWidth: 0,
    plotShadow: false,
    height: "80%",
  },

  title: {
    text: "",
  },

  pane: {
    startAngle: -90,
    endAngle: 89.9,
    background: null,
    center: ["50%", "75%"],
    size: "110%",
  },

  // the value axis
  yAxis: {
    min: 0,
    max: 200,
    tickPixelInterval: 72,
    tickPosition: "inside",
    tickColor: Highcharts.defaultOptions.chart.backgroundColor || "#FFFFFF",
    tickLength: 20,
    tickWidth: 2,
    minorTickInterval: null,
    labels: {
      distance: 20,
      style: {
        fontSize: "14px",
      },
    },
    plotBands: [
      {
        from: 0,
        to: 120,
        color: "#55BF3B", // green
        thickness: 20,
      },
      {
        from: 120,
        to: 160,
        color: "#DDDF0D", // yellow
        thickness: 20,
      },
      {
        from: 160,
        to: 200,
        color: "#DF5353", // red
        thickness: 20,
      },
    ],
  },

  series: [
    {
      name: "Speed",
      data: [80],
      tooltip: {
        valueSuffix: " km/h",
      },
      dataLabels: {
        format: "{y} km/h",
        borderWidth: 0,
        color:
          (Highcharts.defaultOptions.title &&
            Highcharts.defaultOptions.title.style &&
            Highcharts.defaultOptions.title.style.color) ||
          "#333333",
        style: {
          fontSize: "16px",
        },
      },
      dial: {
        radius: "80%",
        backgroundColor: "gray",
        baseWidth: 12,
        baseLength: "0%",
        rearLength: "0%",
      },
      pivot: {
        backgroundColor: "gray",
        radius: 6,
      },
    },
  ],
};
export default {
  components: {
    VueHighcharts,
  },
  data() {
    return {
      options: data,
      Highcharts,
    };
  },
  mounted() {
    const chart = this.$refs.chart.getChart();
    if (!chart.renderer.forExport) {
      timer = setInterval(function () {
        let point = chart.series[0].points[0],
          newVal,
          inc = Math.round((Math.random() - 0.5) * 20);

        newVal = point.y + inc;
        if (newVal < 0 || newVal > 200) {
          newVal = point.y - inc;
        }

        point.update(newVal);
      }, 3000);
    }
  },
  destroyed() {
    if (timer) {
      clearInterval(timer);
    }
  },
};
</script>
<style scoped>
.highcharts-figure,
.highcharts-data-table table {
  min-width: 310px;
  max-width: 500px;
  margin: 1em auto;
}

.highcharts-data-table table {
  font-family: Verdana, sans-serif;
  border-collapse: collapse;
  border: 1px solid #ebebeb;
  margin: 10px auto;
  text-align: center;
  width: 100%;
  max-width: 500px;
}

.highcharts-data-table caption {
  padding: 1em 0;
  font-size: 1.2em;
  color: #555;
}

.highcharts-data-table th {
  font-weight: 600;
  padding: 0.5em;
}

.highcharts-data-table td,
.highcharts-data-table th,
.highcharts-data-table caption {
  padding: 0.5em;
}

.highcharts-data-table thead tr,
.highcharts-data-table tr:nth-child(even) {
  background: #030303;
}

.highcharts-data-table tr:hover {
  background: #0c0c0d;
}
</style>
