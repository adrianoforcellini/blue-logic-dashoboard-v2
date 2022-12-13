<script setup>
import Tractor from "vue-material-design-icons/Tractor.vue";
import ClockOutline from "vue-material-design-icons/ClockOutline.vue";
import ArrowTopRight from "vue-material-design-icons/ArrowTopRight.vue";
import SpeedometerMedium from "vue-material-design-icons/SpeedometerMedium.vue";
import GasStation from "vue-material-design-icons/GasStation.vue";
import Highcharts from "highcharts";
import Gauge from "../components/gauge.vue";

document.addEventListener("DOMContentLoaded", function () {
  Highcharts.chart("container", {
    chart: {
      type: "bar",
      backgroundColor: "none",
    },
    colors: ["#ef5b01"],
    title: {
      text: "L/t",
    },
    xAxis: {
      categories: ["F1", "F2", "F3"],
    },

    series: [
      {
        data: [63, 65, 80],
      },
    ],
  });

  Highcharts.chart("line-container", {
    chart: {
      backgroundColor: "none",
      style: { color: "white", fill: "white" },
    },
    title: {
      text: "",
    },
    colors: ["white", "#008036"],

    subtitle: {
      align: "left",
    },
    legend: false,

    yAxis: {
      title: {},
      type: "linear",
      categories: ["0", "50", "100", "150", "200"],
    },

    xAxis: {
      type: "datetime",
      categories: [
        "06:00",
        "07:00",
        "08:00",
        "09:00",
        "10:00",
        "11:00",
        "12:00",
        "13:00",
        "14:00",
        "15:00",
        "16:00",
      ],
    },

    legend: {
      layout: "vertical",
      align: "right",
      verticalAlign: "middle",
    },

    // plotOptions: {
    //     series: {
    //         label: {
    //             connectorAllowed: false
    //         },
    //     }
    // },

    series: [
      {
        name: "TCH",
        data: [110, 149, 153, 154, 100, 148],
        showInLegend: false,
      },
      {
        name: "Eficiência Operacional",
        data: [80, 83, 98, 99, 82, 84],
        showInLegend: false,
      },
    ],

    responsive: {
      rules: [
        {
          condition: {
            maxWidth: 500,
          },
          chartOptions: {
            legend: {
              layout: "horizontal",
              align: "center",
              verticalAlign: "bottom",
            },
          },
        },
      ],
    },
  });

  const headers = document.getElementsByClassName("card-header");
  for (let header of headers) {
    header.setAttribute("style", "font-weight:bold");
  }

  const texts = document.getElementsByTagName("text");
  for (let text of texts) {
    text.setAttribute("style", "color:white");
    text.setAttribute("style", "fill:white");
  }

  let spams = Array.from(texts).filter(
    (span) => span.innerHTML === "Highcharts.com"
  );
  for (let spam of spams) {
    spam.innerHTML = "";
  }
});
</script>
<template>
  <div class="background w-100 pt-4 ps-3 pe-3">
    <div class="d-flex">
      <div class="container" style="width: 70vw">
        <div>
          <div class="row">
            <b-card
              bg-variant="dark"
              text-variant="white"
              header="TOTAIS"
              class="text-center col-md-7 mt-3"
            >
              <div
                class="line-one"
                style="
                  width: 100%;
                  display: flex;
                  flex-direction: row;
                  margin-top: 10px;
                  margin-left: 15px;
                  font-weight: bold;
                  font-size: 1.1vw;
                  text-align: center;
                "
              >
                <ClockOutline :size="46" />
                <div style="width: 25%; margin-left: 10%">
                  <span>TEMPO TRABALHANDO</span>
                </div>
                <div style="width: 15%; margin-left: 5%">
                  <span>TEMPO OMISSO</span>
                </div>
                <div style="width: 15%; margin-left: 10%">
                  <span>TEMPO OSSIOSO</span>
                </div>
              </div>
              <div
                class="line-two orange-three"
                style="
                  border-radius: 20px;
                  display: flex;
                  flex-direction: row;
                  margin-top: 10px;
                  margin-left: 5px;
                  margin-right: 5px;
                  padding-left: 15px;
                  padding-right: 15px;
                  height: 20%;
                  font-size: 2vw;
                  align-items: center;
                  white-space: nowrap;
                  overflow: hidden;
                  text-overflow: ellipsis;
                "
              >
                <span>Total</span>
                <div style="width: 20%; margin-left: 10%; text-align: center">
                  <span>127 h</span>
                </div>
                <div style="width: 15%; margin-left: 10%; text-align: center">
                  <span>15 h</span>
                </div>
                <div style="width: 15%; margin-left: 10%; text-align: center">
                  <span>10 h</span>
                </div>
              </div>
              <div
                class="line-three orange-two"
                style="
                  border-radius: 20px;
                  display: flex;
                  flex-direction: row;
                  margin-top: 10px;
                  margin-left: 5px;
                  margin-right: 5px;
                  padding-left: 15px;
                  padding-right: 15px;
                  height: 20%;
                  font-size: 1.5vw;
                  align-items: center;
                  white-space: nowrap;
                  overflow: hidden;
                  text-overflow: ellipsis;
                "
              >
                <span>Média</span>
                <div style="width: 15%; margin-left: 15%; text-align: center">
                  <span>12,3 h</span>
                </div>
                <div style="width: 15%; margin-left: 10%; text-align: center">
                  <span>0,3 h</span>
                </div>
                <div style="width: 15%; margin-left: 10%; text-align: center">
                  <span>0,2 h</span>
                </div>
              </div>
            </b-card>
            <div v-if="hasSecondColumn" class="col-md-4 ms-5">
              <b-card
                bg-variant="dark"
                text-variant="white"
                header="EFICIÊNCIA OPERACIONAL"
                class="text-center mt-3"
              >
                <div style="font-size: 3vw" class="mt-4">82%</div>
                <div class="mt-3"><ArrowTopRight :size="46" /></div>
              </b-card>
            </div>
            <div v-else class="col-md-4">
              <b-card
                bg-variant="dark"
                text-variant="white"
                header="EFICIÊNCIA OPERACIONAL"
                class="text-center mt-3"
              >
                <div style="font-size: 3vw" class="mt-4">82%</div>
                <div class="mt-3"><ArrowTopRight :size="46" /></div>
              </b-card>
            </div>
          </div>
        </div>
        <div>
          <b-card-group deck class="row">
            <b-card
              bg-variant="dark"
              text-variant="white"
              header="COMBUSTÍVEL"
              class="text-center col-md-7 mt-4"
            >
              <b-table
                bordered
                striped
                dark
                fixed
                responsive
                :items="items"
                :fields="fields"
              ></b-table>
              <div id="container" style="height: 40vh"></div>
            </b-card>
            <div v-if="hasSecondColumn" class="col-md-4 ms-5">
              <b-card
                bg-variant="dark"
                text-variant="white"
                header="RPM"
                class="text-center mt-4"
              >
                <b-table
                  class="mt-2 mb-4"
                  bordered
                  striped
                  dark
                  fixed
                  responsive
                  :items="rpm_itens"
                  :fields="rpm_fields"
                ></b-table>
              </b-card>

              <b-card
                bg-variant="dark"
                text-variant="white"
                header="VELOCIDADE"
                class="text-center mt-4"
                ><Gauge />
                <div id="speedometer" />
              </b-card>
            </div>
            <div v-else class="col-md-4">
              <b-card
                bg-variant="dark"
                text-variant="white"
                header="RPM"
                class="text-center mt-4"
              >
                <b-table
                  class="mt-2 mb-4"
                  bordered
                  striped
                  dark
                  fixed
                  responsive
                  :items="rpm_itens"
                  :fields="rpm_fields"
                ></b-table>
              </b-card>

              <b-card
                bg-variant="dark"
                text-variant="white"
                header="VELOCIDADE"
                class="text-center mt-4"
                ><Gauge />
                <div id="speedometer" />
              </b-card>
            </div>
          </b-card-group>
        </div>
        <div>
          <b-card-group deck>
            <div class="row">
              <b-card
                bg-variant="dark"
                text-variant="white"
                header="EFICIÊNCIA"
                class="text-center  mt-4"
                style="width: 95%"
              >
                <div style="display: flex; margin-top: 1vw">
                  <div
                    style="
                      background-color: #008036;
                      width: 1.3vw;
                      height: 1.3vw;
                      margin-left: 10%;
                    "
                  />
                  <span style="margin-left: 3%">EFICIÊNCIA OPERACIONAL</span>
                  <div
                    style="
                      background-color: white;
                      width: 1.3vw;
                      height: 1.3vw;
                      margin-left: 10%;
                    "
                  />
                  <span style="margin-left: 3%">THC</span>
                </div>
                <div id="line-container" style="height: 60vh" />
              </b-card>
              <div v-if="!hasSecondColumn" class="mt-3 col-md-8">
                <b-card
                  bg-variant="dark"
                  header="ÁREA TRABALHADA"
                  text-variant="white"
                  class="text-center"
                >
                  <img src="../assets/map.png" class="w-100 mt-3 mb-4" />
                </b-card>
              </div>
            </div>
          </b-card-group>
        </div>
      </div>
      <div
        v-if="hasSecondColumn"
        style="width: 30vw; height: 100vh"
        class="mt-3"
      >
        <b-card
          bg-variant="dark"
          header="ÁREA TRABALHADA"
          text-variant="white"
          class="text-center"
          style="position: fixed"
        >
          <img src="../assets/map.png" class="w-100 mt-3 mb-4" />
        </b-card>
      </div>
    </div>
  </div>
</template>
<style scoped>
.background {
  background-color: rgb(44, 48, 52);
  color: white;
}
.card-header {
  font-weight: bold;
}
.orange-one {
  background-color: rgb(239, 91, 1);
}
.orange-two {
  background-color: rgb(175, 80, 24);
}

.orange-three {
  background-color: rgb(82, 62, 55);
}
</style>
<script>
export default {
  data() {
    return {
      // Note `isActive` is left out and will not appear in the rendered table
      fields: ["Total", "Média"],
      items: [{ Total: "1000 L", Média: "16,3 L/h" }],
      rpm_fields: ["Motor", "Extrator"],
      rpm_itens: [{ Motor: "1452", Extrator: "850" }],
      width: document.documentElement.clientWidth,
      height: document.documentElement.clientHeight,
      hasSecondColumn: true,
    };
  },
  mounted() {
    window.addEventListener("resize", this.getDimensions);
  },
  unmounted() {
    window.removeEventListener("resize", this.getDimensions);
  },
  methods: {
    getDimensions() {
      this.width = document.documentElement.clientWidth;
      this.height = document.documentElement.clientHeight;
      if (this.width < 800) {
        this.hasSecondColumn = false;
      } else {
        this.hasSecondColumn = true;
      }
    },
  },
};
</script>
