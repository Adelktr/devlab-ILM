<template>
  <ParkingCards />
  <Button>Button</Button>
  <BarChart />
  <Map />
</template>

<script>
import BarChart from "./components/Graph.vue";
import ParkingCards from "./components/ParkingCards.vue";
import Map from "./components/Map.vue";
import { Button } from '@/components/ui/button'



export default {
  name: "App",
  components: {Button, BarChart, ParkingCards, Map },
};
</script>

