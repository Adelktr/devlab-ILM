<template>
  <Card v-if="!loading">
    <CardHeader class="flex flex-row items-center justify-between pb-2">
      <CardTitle class="text-sm font-medium">
        {{ collecteData.commune }}
      </CardTitle>
    </CardHeader>
    <CardContent>
      <div class="flex justify-between flex-col gap-y-4 grow">
        <div class="grow">
          <div class="text-sm">Secteur: {{ collecteData.secteur }}</div>
          <div class="text-sm">
            Horaires d'ouverture: {{ collecteData.opening_hours }}
          </div>
          <div class="text-sm">Instructions: {{ collecteData.consigne }}</div>
        </div>

        <Button size="sm">
          <a
            :href="collecteData.url_doc"
            class="text-white hover:text-gray-200 visited:text-purple-600"
            target="_blank"
          >
            Guide des collectes
          </a>
        </Button>
      </div>
    </CardContent>
  </Card>

  <Card v-else>
    <CardHeader class="flex flex-row items-center justify-between pb-2">
      <Skeleton class="w-1/3 h-3 mb-2" />
    </CardHeader>
    <CardContent>
      <div class="flex flex-col items-center gap-y-2">
        <Skeleton class="w-2/3 h-3" />
        <Skeleton class="w-full h-4" />
        <Skeleton class="w-full h-6" />
        <Skeleton class="w-1/2 h-3" />
      </div>
    </CardContent>
  </Card>
</template>

<script>
import { Card, CardHeader, CardContent, CardTitle } from "@/components/ui/card";
import { Skeleton } from "@/components/ui/skeleton";

export default {
  name: "CollecteCard",
  components: {
    Card,
    CardHeader,
    CardContent,
    CardTitle,
    Skeleton,
  },
  props: {
    collecteData: {
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
