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
            backgroundColor: "#f87979",
            data: [11171761.019999998, 15151088.719999999, 21185701.019999996, 13884670.240000043, 29930326.989999995, -12140233.930000003
              ,7870404.439999968, -21808018.45999999, -445295.9099999964, -7070946.580000013, 4046840.3000000045, 717076.9400000032
              , -24274091.93, 6798368.88, -23734187.08, -1858822.339999985, -7389095.729999989, 8455210.320000008],
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
        this.dataTest.push(budgetData[i].resultat_exercice);
        console.log(budgetData[i].resultat_exercice);

      }

      for (let i = 0; i < this.chartData.datasets.length; i++) {
        const dataset = this.chartData.datasets[i];
        this.dataTest.forEach((newData) => {
          dataset.data.push(newData);
        });
      }
      this.$refs.myChart.update();
    },
  },
  async created() {
    await this.fetchData();
  },
};
</script>