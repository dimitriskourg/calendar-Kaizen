<template>
  <div
    @click="handleTileClick"
    class="rounded-lg p-2 flex flex-col items-center justify-center backdrop-blur-sm border-2 transition-colors cursor-pointer w-32 h-32"
    :class="[statusClasses, selectedMatrixTileClasses]"
  >
    <span class="text-gray-400 text-xs"> {{ title }} </span>
    <span class="text-xl font-bold text-white"> {{ subtitle }} </span>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  id: Number,
  title: String,
  subtitle: String,
  status: String,
  showOffersFn: Function,
  isMatrixTileSelected: Boolean,
})

const statusClasses = computed(() =>
  props.status === 'locked' ? 'opacity-50 cursor-not-allowed' : 'hover:border-purple-500/50',
)

const selectedMatrixTileClasses = computed(() =>
  props.isMatrixTileSelected ? 'bg-indigo-900/60 border-0 rounded-b-none' : '',
)

const handleTileClick = () => {
  if (props.status === 'locked') return
  props.showOffersFn(props.id)
}
</script>

<style lang="scss" scoped></style>
