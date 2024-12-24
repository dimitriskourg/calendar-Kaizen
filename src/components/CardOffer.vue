<template>
  <div
    class="border-purple-500/20 p-4 bg-indigo-900/60 rounded-lg rounded-tr-none"
  >
    <div class="flex items-center gap-4">
      <div class="image w-16 h-16 rounded-lg bg-slate-400"></div>
      <div class="flex-1">
        <div class="flex items-center gap-2 mb-2">
          <span class="text-xs px-2 py-0.5 rounded text-slate-300" :class="[offerStatusClasses]">{{
            offer.label
          }}</span>
        </div>
        <h3 class="text-white font-medium">{{ offer.title }}</h3>
        <p class="text-purple-300 text-sm">💰 {{ offer.amount }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
const props = defineProps({
  offer: Object,
  onNavigate: Function,
})

const offerStatusClasses = computed(() => ({
  'bg-green-500/20': props?.offer.label === 'WON',
  'bg-red-500/20': props?.offer.label === 'LOST',
}))
</script>

<style lang="scss" scoped></style>
