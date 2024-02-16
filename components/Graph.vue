<template>
  <Bar v-if="chartData.datasets[0].data.length" id="my-chart-id" ref="myChart" :data="chartData" />
</template>

<script>
import { Bar } from "vue-chartjs";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

export default {
  name: "BarChart",
  components: { Bar },
  data() {
    return {
      // budgetData: [],
      loading: false,
      chartData: {
        labels: [],
        datasets: [
          {
            label: "Résultat exercice",
            borderColor: "#059669",
            backgroundColor: "#6EE7B7",
            data: [],
          },
        ],
      },
    };
  },

  methods: {
    async fetchData() {
      const url =
        "https://data.issy.com/api/explore/v2.1/catalog/datasets/resultats-des-exercices-budgetaires-a-issy/records?limit=20";

      const response = await fetch(url);
      let budgetData = await response.json()
      let data = budgetData.results
      let resultats = [];

      for (let i = 0; i < data.length; i++) {
        this.chartData.labels.push(data[i].exercice);
        resultats.push(data[i].resultat_exercice);
      }
      this.chartData.datasets[0].data = resultats;

      console.log(this.chartData.datasets[0]);

      //const dataset = this.chartData.datasets[0];

      // this.chartData.datasets[0].data = this.dataTest;

      //this.dataTest.forEach((newData) => {
      //  dataset.data.push(newData);
      //});

      // this.$refs.myChart.update();
    },
  },
  async created() {
    await this.fetchData();
  },
};
</script>
