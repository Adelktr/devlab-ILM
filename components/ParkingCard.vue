<template>
  <Card v-if="!loading">
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <CardTitle class="text-sm font-medium">
        {{ parkingData.name }}
      </CardTitle>
    </CardHeader>
    <CardContent>
      <HoverCard>
        <HoverCardTrigger>
          <div class="flex flex-col items-center">
          <span>
            {{ parkingData.value_free_spots }} /
            {{ parkingData.nombre_de_places_contractuelles }}
          </span>
            <Progress :model-value="parkingData.remplissage" />
          </div>
        </HoverCardTrigger>
        <HoverCardContent>
          {{ parkingData.remplissage ? "Parking plein" : `${parkingData.value_free_spots} places disponibles` }}
        </HoverCardContent>
      </HoverCard>
    </CardContent>
  </Card>

  <Card v-else>
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <Skeleton class="w-1/3 h-3 mb-2" />
    </CardHeader>
    <CardContent>
      <HoverCard>
        <HoverCardTrigger>
          <div class="flex flex-col items-center gap-y-2">
            <Skeleton class="w-1/3 h-3" />
            <Skeleton class="w-full h-4 rounded-full" />
          </div>
        </HoverCardTrigger>
        <HoverCardContent>
          Chargement...
        </HoverCardContent>
      </HoverCard>
    </CardContent>
  </Card>


</template>
<script>

import {Card, CardHeader, CardContent, CardTitle, CardFooter} from "@/components/ui/card"
import {Progress} from "@/components/ui/progress";
import {HoverCard, HoverCardContent, HoverCardTrigger} from "@/components/ui/hover-card";
import { Skeleton } from '@/components/ui/skeleton'


export default {
  name: "Card",
  components: {
    Skeleton,
    HoverCard,
    Progress,
    Card,
    CardHeader,
    CardContent,
    CardTitle,
    CardFooter,
    HoverCardContent,
    HoverCardTrigger
  },
  props: {
    parkingData: {
      type: Object,
      default: {},
    },
    loading: {
      type: Boolean,
      default: false,
    },
  }
};
</script>
