<template>
  <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
    <FacilityCard
      v-for="(data, index) in facilityData"
      :key="index"
      :facility-data="data"
      :loading="loading"
    />
  </div>
</template>
<script>
import Card from "@/components/FacilityCard.vue";
export default {
  name: "FacilityCards",
  components: {
    Card,
  },
  data() {
    return {
      facilityData: [5] | [],
      loading: false,
    };
  },

  async created() {
    this.loading = true;
    const url =
      "https://data.issy.com/api/explore/v2.1/catalog/datasets/decheteries-fixes/records?limit=40";

    try {
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`Erreur HTTP: ${response.status}`);
      }
      this.facilityData = await response.json();
      this.facilityData = this.facilityData.results;
      this.loading = false;
    } catch (error) {
      console.error("Erreur lors de la récupération des données:", error);
      this.loading = false;
    }
  },
};
</script>
