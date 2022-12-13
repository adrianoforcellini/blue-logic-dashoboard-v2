<script setup>
import Tractor from "vue-material-design-icons/Tractor.vue";
import ClockOutline from "vue-material-design-icons/ClockOutline.vue";
import ArrowTopRight from "vue-material-design-icons/ArrowTopRight.vue";
import SpeedometerMedium from "vue-material-design-icons/SpeedometerMedium.vue";
import GasStation from "vue-material-design-icons/GasStation.vue";
import Highcharts from "highcharts";
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

//   Highcharts.chart("line-container", {
//     chart: {
//       backgroundColor: "none",
//       style: { color: "white", fill: "white" },
//     },
//     title: {
//       text: "Gráfico de Eficiência",
//     },
//     colors: ["white", "#008036"],

//     subtitle: {
//       align: "left",
//     },
//     legend: false,

//     yAxis: {
//       title: {},
//       type: "linear",
//       categories: ["0", "50", "100", "150", "200"],
//     },

//     xAxis: {
//       type: "datetime",
//       categories: [
//         "06:00",
//         "07:00",
//         "08:00",
//         "09:00",
//         "10:00",
//         "11:00",
//         "12:00",
//         "13:00",
//         "14:00",
//         "15:00",
//         "16:00",
//       ],
//     },

//     legend: {
//       layout: "vertical",
//       align: "right",
//       verticalAlign: "middle",
//     },

//     // plotOptions: {
//     //     series: {
//     //         label: {
//     //             connectorAllowed: false
//     //         },
//     //     }
//     // },

//     series: [
//       {
//         name: "TCH",
//         data: [110, 149, 153, 154, 100, 148],
//         showInLegend: false,
//       },
//       {
//         name: "Eficiência Operacional",
//         data: [80, 83, 98, 99, 82, 84],
//         showInLegend: false,
//       },
//     ],

//     responsive: {
//       rules: [
//         {
//           condition: {
//             maxWidth: 500,
//           },
//           chartOptions: {
//             legend: {
//               layout: "horizontal",
//               align: "center",
//               verticalAlign: "bottom",
//             },
//           },
//         },
//       ],
//     },
//   });
//   const texts = document.getElementsByTagName("text");
//   for (let text of texts) {
//     text.setAttribute("style", "color:white");
//     text.setAttribute("style", "fill:white");
//   }

//   let spams = Array.from(texts).filter(span => span.innerHTML === 'Highcharts.com')
//   for ( let spam  of spams) {
//     spam.innerHTML=""
//   }

});
</script>

<template>
  <div class="d-flex">
    <div class="container w-75">
      <div>
        <div class="row">
          <b-card
            bg-variant="dark"
            text-variant="white"
            header="TOTAIS"
            class="text-center col-md-8"
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
              <div style="width: 20%; margin-left: 10%">
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
              "
            >
              <span>Total</span>
              <div style="width: 15%; margin-left: 65px; text-align: center">
                <span>127 h</span>
              </div>
              <div style="width: 15%; margin-left: 65px; text-align: center">
                <span>15 h</span>
              </div>
              <div style="width: 15%; margin-left: 65px; text-align: center">
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
              "
            >
              <span>Média</span>
              <div style="width: 15%; margin-left: 65px; text-align: center">
                <span>12,3 h</span>
              </div>
              <div style="width: 15%; margin-left: 65px; text-align: center">
                <span>0,3 h</span>
              </div>
              <div style="width: 15%; margin-left: 65px; text-align: center">
                <span>0,2 h</span>
              </div>
            </div>
          </b-card>

          <b-card
            bg-variant="dark"
            text-variant="white"
            header="EFICIÊNCIA OPERACIONAL"
            class="text-center col-md-3 ms-1"
          >
            <div style="font-size: 3vw">82%</div>
            <div class="mt-3"><ArrowTopRight :size="46" /></div>
          </b-card>
        </div>
      </div>
      <div>
        <b-card-group deck class="row mt-5">
          <b-card
            bg-variant="dark"
            text-variant="white"
            header="COMBUSTÍVEL"
            class="text-center col-md-8"
          >

              <b-table bordered striped  dark fixed responsive :items="items" :fields="fields" ></b-table>
              <div id="container"></div>

          </b-card>
          <div class="col-md-3">
            <b-card
              bg-variant="dark"
              text-variant="white"
              header="Warning"
              class="text-center"
            >
              <b-card-text
                >Lorem ipsum dolor sit amet, consectetur adipiscing
                elit.</b-card-text
              >
            </b-card>

            <b-card
              bg-variant="dark"
              text-variant="white"
              header="Danger"
              class="text-center"
            >
              <b-card-text
                >Lorem ipsum dolor sit amet, consectetur adipiscing
                elit.</b-card-text
              >
            </b-card>
          </div>
        </b-card-group>
      </div>
      <div>
        <b-card-group deck>
          <b-card
            bg-variant="dark"
            text-variant="white"
            header="Light"
            class="text-center"
          >
            <b-card-text
              >Lorem ipsum dolor sit amet, consectetur adipiscing
              elit.</b-card-text
            >
          </b-card>

          <b-card
            bg-variant="dark"
            header="Dark"
            text-variant="white"
            class="text-center"
          >
            <b-card-text
              >Lorem ipsum dolor sit amet, consectetur adipiscing
              elit.</b-card-text
            >
          </b-card>

          <b-card
            bg-variant="dark"
            header="Default"
            text-variant="white"
            class="text-center"
          >
            <b-card-text
              >Lorem ipsum dolor sit amet, consectetur adipiscing
              elit.</b-card-text
            >
          </b-card>
        </b-card-group>
      </div>
    </div>
    <div class="container w-25">
      <b-card
        bg-variant="dark"
        header="Default"
        text-variant="white"
        class="text-center"
      >
        <b-card-text
          >Lorem ipsum dolor sit amet, consectetur adipiscing elit.</b-card-text
        >
      </b-card>
    </div>
  </div>
</template>
<style scoped>
/* .background {
  background-color: rgb(67, 79, 91);
  color: white;
} */
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
        fields: ['Total', 'Média'],
        items: [
          { Total: '1000 L', Média: '16,3 L/h' },
        ]
      }
    }
  }
</script>