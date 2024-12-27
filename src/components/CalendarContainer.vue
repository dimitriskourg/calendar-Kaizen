<template>
  <div class="min-h-screen bg-gray-900 bg-cover bg-center bg-no-repeat">
    <div class="min-h-screen bg-gray-900/70 backdrop-blur-sm py-8">
      <MatrixTileList
        :tiles="tileData"
        :showSelectedTileOffers="handleTileClick"
        :selectedTileId="selectedTileId"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import MatrixTileList from './MatrixTileList.vue'
const tileData = ref([
  {
    id: 1,
    title: 'Dec',
    subtitle: '01',
    status: 'won',
    offer: {
      id: '1',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 2,
    title: 'Dec',
    subtitle: '02',
    status: 'lost',
    offer: {
      id: '2',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
  {
    id: 3,
    title: 'Dec',
    subtitle: '03',
    status: 'won',
    offer: {
      id: '3',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 4,
    title: 'Dec',
    subtitle: '04',
    status: 'lost',
    offer: {
      id: '4',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
  {
    id: 5,
    title: 'Dec',
    subtitle: '05',
    status: 'won',
    offer: {
      id: '5',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 6,
    title: 'Dec',
    subtitle: '06',
    status: 'lost',
    offer: {
      id: '6',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
  {
    id: 7,
    title: 'Dec',
    subtitle: '07',
    status: 'won',
    offer: {
      id: '7',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 8,
    title: 'Dec',
    subtitle: '08',
    status: 'lost',
    offer: {
      id: '8',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
  {
    id: 9,
    title: 'Dec',
    subtitle: '09',
    status: 'current',
    offer: {
      id: '9',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 10,
    title: 'Dec',
    subtitle: '10',
    status: 'locked',
    offer: {
      id: '10',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
  {
    id: 11,
    title: 'Dec',
    subtitle: '11',
    status: 'locked',
    offer: {
      id: '11',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 12,
    title: 'Dec',
    subtitle: '12',
    status: 'locked',
    offer: {
      id: '12',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
  {
    id: 13,
    title: 'Dec',
    subtitle: '13',
    status: 'locked',
    offer: {
      id: '13',
      title: 'An offer',
      amount: '100.000€',
      label: 'WON',
    },
  },
  {
    id: 14,
    title: 'Dec',
    subtitle: '14',
    status: 'locked',
    offer: {
      id: '14',
      title: 'Another offer',
      amount: '50.000€',
      label: 'LOST',
    },
  },
])

const selectedTile = ref(null)

const handleTileClick = (id) => {
  console.log('handleTileClick', id)
  selectedTile.value = tileData.value.find((tile) => tile.id === id)
}

const selectedTileId = computed(() => selectedTile.value?.id)
</script>

<style lang="scss" scoped></style>
