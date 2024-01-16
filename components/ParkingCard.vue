<template>
  <Card>
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <CardTitle class="text-sm font-medium">
        {{ parkingData.name }}
      </CardTitle>
    </CardHeader>
    <CardContent>
      <div class="flex flex-col items-center">
        <span>
          {{ parkingData.value_free_spots }} /
          {{ parkingData.nombre_de_places_contractuelles }}
        </span>
        <Progress :model-value="parkingData.remplissage" />
      </div>
    </CardContent>
  </Card>


</template>
<script>

import {Card, CardHeader, CardContent, CardTitle, CardFooter} from "@/components/ui/card"
import {Progress} from "@/components/ui/progress";


export default {
  name: "Card",
  components: {
    Progress,
    Card,
    CardHeader,
    CardContent,
    CardTitle,
    CardFooter,
  },
  props: {
    parkingData: {
      type: Object,
      default: {},
    },
  }
};
</script>
