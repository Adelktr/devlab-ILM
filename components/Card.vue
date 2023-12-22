<template>
  <!-- <div class="flex items-start justify-between">
    <p>Parking name : {{ parkingData.name }}</p>
    <p>Place totale : {{ parkingData.nombre_de_places_contractuelles }}</p>
    <p>Place libres : {{ parkingData.value_free_spots }}</p>
  </div> -->
  <div
    class="bg-slate-600 w-1/4 rounded-lg flex justify-center flex-col items-center p-2"
  >
    <p class="font-normal text-gray-700 dark:text-gray-400">
      {{ parkingData.name }}
    </p>
    <p class="mb-2 text-2xl font-bold tracking-tight text-white">
      {{ parkingData.value_free_spots }} /
      {{ parkingData.nombre_de_places_contractuelles }}
    </p>
    <div class="w-full bg-gray-200 rounded-full h-1.5 mb-4 dark:bg-gray-700">
      <div
        class="bg-blue-600 h-1.5 rounded-full dark:bg-blue-500"
        :style="getWidthProgressBar()"
      ></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  props: {
    parkingData: {
      type: Object,
      default: {},
    },
  },
  methods: {
    getWidthProgressBar() {
      const value =
        (50 * 100) / this.parkingData.nombre_de_places_contractuelles;
      return `width: ${value}%`;
    },
  },
};
</script>
