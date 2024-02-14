<template>
  <Bar id="my-chart-id" ref="myChart" :data="chartData" />
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
      budgetData: [],
      dataTest: [],
      loading: false,
      chartData: {
        labels: [],
        datasets: [
          {
            label: "Résultat exercice",
            borderColor: "#059669",
            backgroundColor: "#A7F3D0",
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
      let budgetData = await response.json();
      budgetData = budgetData.results;

      for (let i = 0; i < budgetData.length; i++) {
        this.chartData.labels.push(budgetData[i].exercice);
        // this.chartData.datasets[0].data = [...this.chartData.datasets[0].data, budgetData[i].resultat_exercice];
        this.dataTest = [...this.dataTest, budgetData[i].resultat_exercice];

      }

      console.log(this.chartData)
      const dataset = this.chartData.datasets[0];

      // this.chartData.datasets[0].data = this.dataTest;
      
      this.dataTest.forEach((newData) => {
        dataset.data.push(newData);
      });

      // this.$refs.myChart.update();
    },
  },
  async created() {
    await this.fetchData();
  },
};
</script>