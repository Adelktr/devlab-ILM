<template>
  <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
    <CollecteCard
      v-for="(data, index) in collecteData"
      :key="index"
      :collecte-data="data"
      :loading="loading"
    />
  </div>
</template>
<script>
import Card from "@/components/CollecteCard.vue";
export default {
  name: "CollecteCards",
  components: {
    Card,
  },
  data() {
    return {
      collecteData: [5] | [],
      loading: false,
    };
  },

  async created() {
    this.loading = true;
    const url =
      "https://data.issy.com/api/explore/v2.1/catalog/datasets/gpso_prop_secteur_encombrant/records?limit=40";

    try {
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`Erreur HTTP: ${response.status}`);
      }
      this.collecteData = await response.json();
      this.collecteData = this.collecteData.results;
      this.loading = false;
    } catch (error) {
      console.error("Erreur lors de la récupération des données:", error);
      this.loading = false;
    }
  },
};
</script>
