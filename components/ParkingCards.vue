<template>
  <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
    <ParkingCard
      v-for="(data, index) in parkingData"
      :key="index"
      :parking-data="data"
      :loading="loading"
    />
  </div>
</template>
<script>
import Card from "@/components/ParkingCard.vue";
import * as _ from "lodash";
export default {
  name: "ParkingCards",
  components: {
    Card,
  },
  data() {
    return {
      parkingData: [5] | [],
      loading: false,
    };
  },

  async created() {
    this.loading = true;
    const url =
      "https://data.issy.com/api/explore/v2.1/catalog/datasets/park-indigo-disponibilite-temps-reel/records?limit=4";

    try {
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`Erreur HTTP: ${response.status}`);
      }
      this.parkingData = await response.json();
      this.parkingData = this.parkingData.results;
      this.parkingData = this.parkingData.map((parking) => {
        const randomInt = _.random(10, 176);
        return {
          ...parking,
          remplissage:
            (randomInt / parking.nombre_de_places_contractuelles) * 100,
          value_free_spots: randomInt,
        };
      });
      this.loading = false;
    } catch (error) {
      console.error("Erreur lors de la récupération des données:", error);
      this.loading = false;
    }
  },
};
</script>
