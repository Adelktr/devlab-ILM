<template>
  <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
    <RentCard
      v-for="(data, index) in rentData"
      :key="index"
      :rent-data="data"
      :loading="loading"
    />
  </div>
</template>
<script>
import Card from "@/components/RentCard.vue";
export default {
  name: "RentCards",
  components: {
    Card,
  },
  data() {
    return {
      rentData: [5] | [],
      loading: false,
    };
  },

  async created() {
    this.loading = true;
    const url =
      "https://data.issy.com/api/explore/v2.1/catalog/datasets/locationdesallespourdesevenements-feuille1/records?limit=40";

    try {
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`Erreur HTTP: ${response.status}`);
      }
      this.rentData = await response.json();
      this.rentData = this.rentData.results;
      this.loading = false;
    } catch (error) {
      console.error("Erreur lors de la récupération des données:", error);
      this.loading = false;
    }
  },
};
</script>
