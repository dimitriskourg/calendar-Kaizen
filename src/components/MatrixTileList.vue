<template>
  <div class="w-full max-w-md mx-auto p-4">
    <h1 class="text-4xl font-bold text-center mb-8 text-purple-300 drop-shadow-glow">
      Dia de Muertos
    </h1>
    <div class="grid grid-cols-3 justify-center gap-x-4 grid-flow-dense">
      <template v-for="tile in tiles" :key="tile.id">
        <MatrixTile
          :showOffersFn="(id) => showSelectedTileOffers(id)"
          :id="tile.id"
          :title="tile.title"
          :subtitle="tile.subtitle"
          :status="tile.status"
          :isMatrixTileSelected="selectedTileId === tile.id"
        />
        <!-- <CardOffer :offer="tile.offer" v-if="selectedTileId === tile.id" class="col-span-full" /> -->
        <div v-if="selectedTileId === tile.id" class="col-span-full h-4 flex">
          <div class="w-[272px] h-4"></div>
          <SeparatorCurve class="h-4 w-4" />
          <div class="bg-indigo-900/60 w-32 h-4"></div>
        </div>
        <CardOffer :offer="tile.offer" v-if="selectedTileId === tile.id" class="col-span-full" />
        <div v-if="tile.id % 3 === 0" class="col-span-full h-4"></div>
      </template>
    </div>
  </div>
</template>

<script setup>
import CardOffer from './CardOffer.vue'
import MatrixTile from './MatrixTile.vue'
import SeparatorCurve from './SeparatorCurve.vue'

defineProps({
  tiles: Array,
  showSelectedTileOffers: Function,
  selectedTileId: Number,
})
</script>

<style lang="scss" scoped></style>
