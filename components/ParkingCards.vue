<template>
  <div class="flex gap-10 px-4 mt-4">
    <Card
      v-for="(data, index) in parkingData"
      :key="index"
      :parking-data="data"
    />
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "ParkingCards",
  components: {
    Card,
  },
  data() {
    return {
      parkingData: [],
    };
  },

  async created() {
    const url =
      "https://data.issy.com/api/explore/v2.1/catalog/datasets/park-indigo-disponibilite-temps-reel/records?limit=40";

    try {
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`Erreur HTTP: ${response.status}`);
      }
      this.parkingData = await response.json();
      this.parkingData = this.parkingData.results;
    } catch (error) {
      console.error("Erreur lors de la récupération des données:", error);
    }
  },
};
</script>
