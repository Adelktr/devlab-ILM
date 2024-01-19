<script lang="ts">
import BarChart from "@/components/Graph.vue";
import ParkingCards from "@/components/ParkingCards.vue";
import Map from "@/components/Map.vue";

import Search from '@/components/Search.vue'

// Shadcn-ui components
import { Button } from '@/components/ui/button'
import { Tabs, TabsList, TabsTrigger, TabsContent } from '@/components/ui/tabs'
import { Card, CardHeader, CardTitle, CardDescription, CardContent } from '@/components/ui/card'
import { HoverCard, HoverCardTrigger, HoverCardContent } from '@/components/ui/hover-card'

export default {
  name: "Dashboard",
  components: {
    BarChart,
    ParkingCards,
    Map,
    Search,
    Button,
    Tabs,
    TabsList,
    TabsTrigger,
    TabsContent,
    Card,
    CardHeader,
    CardTitle,
    CardDescription,
    CardContent,
    HoverCard,
    HoverCardTrigger,
    HoverCardContent
  },
};
</script>

<template>
  <div class="hidden flex-col md:flex">
    <div class="border-b">
      <div class="flex justify-between h-16 items-center px-4">
          <img src="/logo.png" alt="Issy les Moulineaux logo" class="h-14" />
          <Search />
      </div>
    </div>

    <div class="flex-1 space-y-4 p-8 pt-6">
      <div class="flex items-center justify-between space-y-2">
        <h2 class="text-3xl font-bold tracking-tight">
          Dashboard
        </h2>
        <div class="flex items-center space-x-2">
          <Button size="sm">
            Reload page
          </Button>
        </div>
      </div>
      <Tabs default-value="overview" class="space-y-4">
        <TabsList>
          <TabsTrigger value="overview">
            Overview
          </TabsTrigger>
          <TabsTrigger value="analytics">
            Util1
          </TabsTrigger>
          <TabsTrigger value="reports">
            Util2
          </TabsTrigger>
          <TabsTrigger value="notifications">
            Util3
          </TabsTrigger>
        </TabsList>

        <TabsContent value="overview" class="space-y-4">
          <ParkingCards />
          <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-7">
            <Card class="col-span-4">
              <CardHeader>
                <CardTitle>Overview</CardTitle>
                <CardDescription>
                  Carte de la ville avec de la donnée provenant de l'API
                </CardDescription>
              </CardHeader>
              <CardContent class="pl-2">
                <HoverCard>
                  <HoverCardTrigger>
                    <Map />
                  </HoverCardTrigger>
                  <HoverCardContent>
                    Une carte représentant les informations de Issy les Moulineaux
                  </HoverCardContent>
                </HoverCard>
              </CardContent>
            </Card>
            <Card class="col-span-3">
              <CardHeader>
                <CardTitle>Stats</CardTitle>
                <CardDescription>
                  Statistiques de la ville (Fausse données pour le moment)
                </CardDescription>
              </CardHeader>
              <CardContent>
                <BarChart />
              </CardContent>
            </Card>
          </div>
        </TabsContent>
      </Tabs>
    </div>
  </div>
</template>

<style scoped>

</style>