<template>
  <Card v-if="!loading">
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <CardTitle class="text-sm font-medium">
        {{ rentData.nom }}
      </CardTitle>
    </CardHeader>
    <CardContent>
      <div class="space-y-4">
        <div class="text-sm">{{ rentData.description }}</div>
        <div class="text-sm">Capacité: {{ rentData.capacite_de_la_salle }} personnes</div>
        <div class="text-sm">Adresse: {{ rentData.adresse }}, {{ rentData.code_postal }} {{ rentData.ville }}</div>
        <div class="text-sm">Téléphone: {{ rentData.telephone }}</div>
        <div class="text-sm">Site Web: <a href="{{ rentData.site_web }}" target="_blank" rel="noopener noreferrer">{{ rentData.site_web }}</a></div>
        <Button size="sm">
        <div class="text-sm">Contact: <a href="{{ rentData.contact_en_ligne }}" target="_blank" rel="noopener noreferrer">Formulaire en ligne</a></div>
        </Button>
      </div>
    </CardContent>
  </Card>

  <Card v-else>
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <Skeleton class="w-1/3 h-3 mb-2" />
    </CardHeader>
    <CardContent>
      <div class="flex flex-col gap-y-2">
        <Skeleton class="w-full h-6" />
        <Skeleton class="w-full h-4" />
        <Skeleton class="w-full h-4" />
        <Skeleton class="w-full h-4" />
        <Skeleton class="w-full h-4" />
        <Skeleton class="w-full h-4" />
      </div>
    </CardContent>
  </Card>
</template>

<script>
import {Card, CardHeader, CardContent, CardTitle} from "@/components/ui/card";
import { Skeleton } from '@/components/ui/skeleton';

export default {
  name: "RentCard",
  components: {
    Card,
    CardHeader,
    CardContent,
    CardTitle,
    Skeleton
  },
  props: {
    rentData: {
      type: Object,
      default: () => ({}),
    },
    loading: {
      type: Boolean,
      default: false,
    },
  }
};
</script>
