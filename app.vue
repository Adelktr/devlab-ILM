<script lang="ts">
import BarChart from "@/components/Graph.vue";
import ParkingCards from "@/components/ParkingCards.vue";
import FacilityCards from "@/components/FacilityCards.vue";
import Map from "@/components/Map.vue";

import Search from "@/components/Search.vue";

// Shadcn-ui components
import {
  Table,
  TableCaption,
  TableHeader,
  TableRow,
  TableHead,
  TableCell,
  TableBody,
} from "@/components/ui/table";

import { Button } from "@/components/ui/button";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import {
  Card,
  CardHeader,
  CardTitle,
  CardDescription,
  CardContent,
} from "@/components/ui/card";
import {
  HoverCard,
  HoverCardTrigger,
  HoverCardContent,
} from "@/components/ui/hover-card";

import { Badge } from "@/components/ui/badge";
export default {
  name: "Dashboard",
  components: {
    BarChart,
    ParkingCards,
    FacilityCards,
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
    HoverCardContent,
    Table,
    TableCaption,
    TableHeader,
    TableRow,
    TableHead,
    TableCell,
    TableBody,
    Badge,
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
        <h2 class="text-3xl font-bold tracking-tight">Dashboard</h2>
        <div class="flex items-center space-x-2">
          <Button size="sm"> Reload page </Button>
        </div>
      </div>
      <Tabs default-value="overview" class="space-y-4">
        <TabsList>
          <TabsTrigger value="overview">
            Overview
          </TabsTrigger>
          <TabsTrigger value="analytics">
            Déchèteries
          </TabsTrigger>
          <TabsTrigger value="reports">
            Collecte des Encombrants
          </TabsTrigger>
          <TabsTrigger value="notifications">
            Réservation de salles
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
                    Une carte représentant les informations de Issy les
                    Moulineaux
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
          <div>
            <Card>
              <CardHeader>
                <CardTitle>Parkings</CardTitle>
                <CardDescription>
                  Liste des parkings et leur données
                </CardDescription>
              </CardHeader>
              <CardContent>
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead className="w-[100px]">Nom</TableHead>
                      <TableHead>Status</TableHead>
                      <TableHead>Places Libres</TableHead>
                      <TableHead>Places Max</TableHead>
                      <TableHead>Adresse</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    <TableRow>
                      <TableCell className="font-medium"
                        >Point du Jour</TableCell
                      >
                      <TableCell>
                        <Badge
                          variant="outline"
                          class="bg-green-50 text-green-500 border-green-200"
                          >Ouvert</Badge
                        >
                      </TableCell>
                      <TableCell>50</TableCell>
                      <TableCell className="text-right">525</TableCell>
                      <TableCell className="text-right"
                        >Place Abel Gance</TableCell
                      >
                    </TableRow>
                    <TableRow>
                      <TableCell className="font-medium"
                        >Camille Desmoulins</TableCell
                      >
                      <TableCell
                        ><Badge
                          variant="outline"
                          class="bg-red-50 text-red-500 border-red-200"
                          >Fermé</Badge
                        ></TableCell
                      >

                      <TableCell>0</TableCell>
                      <TableCell className="text-right">176</TableCell>
                      <TableCell className="text-right"
                        >56, Rue Camille Desmoulins</TableCell
                      >
                    </TableRow>
                    <TableRow>
                      <TableCell className="font-medium"
                        >Ile Saint Germain</TableCell
                      >
                      <TableCell>
                        <Badge
                          variant="outline"
                          class="bg-green-50 text-green-500 border-green-200"
                          >Ouvert</Badge
                        ></TableCell
                      >
                      <TableCell>16</TableCell>
                      <TableCell className="text-right">177</TableCell>
                      <TableCell className="text-right"
                        >169 Bis, Quai de Stalingrad</TableCell
                      >
                    </TableRow>
                    <TableRow>
                      <TableCell className="font-medium"
                        >Hôtel de Ville
                      </TableCell>
                      <TableCell>
                        <Badge
                          variant="outline"
                          class="bg-orange-50 text-orange-500 border-orange-200"
                          >Ferme bientôt</Badge
                        ></TableCell
                      >
                      <TableCell>2</TableCell>
                      <TableCell className="text-right">270</TableCell>
                      <TableCell className="text-right"
                        >60, rue du Général Leclerc</TableCell
                      >
                    </TableRow>
                  </TableBody>
                </Table>
              </CardContent>
            </Card>
          </div>
        </TabsContent>

        <TabsContent value="analytics" class="space-y-4">
          <FacilityCards />
          <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-7">
            <Card class="col-span-4">
              <CardHeader>
                <CardTitle>Analytics</CardTitle>
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

        <TabsContent value="reports" class="space-y-4">
          <CollecteCards />
          <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-7">
            <Card class="col-span-4">
              <CardHeader>
                <CardTitle>Collecte des Encombrants</CardTitle>
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

        <TabsContent value="notifications" class="space-y-4">
          <RentCards />
          <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-7">
            <Card class="col-span-4">
              <CardHeader>
                <CardTitle>Salles à louer</CardTitle>
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

<style scoped></style>

</style>