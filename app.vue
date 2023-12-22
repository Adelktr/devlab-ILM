<template>
  <ParkingCards />
  <BarChart />
  <Map />
</template>

<script>
import BarChart from "./components/Graph.vue";
import ParkingCards from "./components/ParkingCards.vue";
import Map from "./components/Map.vue";

export default {
  name: "App",
  components: { BarChart, ParkingCards, Map },
};
</script>
