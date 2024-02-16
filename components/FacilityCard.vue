<template>
  <Card v-if="!loading && facilityData">
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <CardTitle class="text-sm font-medium">
        {{ facilityData.nom }}
      </CardTitle>
    </CardHeader>
    <CardContent>
      <div class="space-y-4 h-full flex flex-col justify-between">
        <div class="grow">
          <p><strong>Commune:</strong> {{ facilityData.commune }}</p>
          <p><strong>Localisation:</strong> {{ facilityData.localisation }}</p>
          <p><strong>Modalités d'accès:</strong> {{ facilityData.modalite_acces }}</p>
          <p><strong>Horaires:</strong> {{ facilityData.horaire }}</p>
          <p><strong>Volume Max:</strong> {{ facilityData.volume }}</p>
        </div>
        <Button size="sm">
          <a :href="facilityData.url_doc" target="_blank">Plus d'informations</a>
        </Button>
      </div>
    </CardContent>
  </Card>

  <Card v-else>
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <Skeleton class="w-1/3 h-3 mb-2" />
    </CardHeader>
    <CardContent>
      <div class="flex flex-col items-center gap-y-2">
        <Skeleton class="w-1/3 h-3" />
        <Skeleton class="w-full h-4 rounded-full" />
        <Skeleton class="w-full h-3 rounded-full" />
      </div>
    </CardContent>
  </Card>
</template>

<script>
import {Card, CardHeader, CardContent, CardTitle} from "@/components/ui/card"
import { Skeleton } from '@/components/ui/skeleton'

export default {
  name: "FacilityCard",
  components: {
    Skeleton,
    Card,
    CardHeader,
    CardContent,
    CardTitle,
  },
  props: {
    facilityData: {
      type: Object,
      default: () => ({}),
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
