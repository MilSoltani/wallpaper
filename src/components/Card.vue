<script setup>
defineProps({
  title: {
    type: String,
    default: 'header'
  },
  items: {
    type: Array,
    default: () => []
  }
})
</script>

<template>
  <div class="border border-red-500 rounded-xl h-[330px] flex flex-col">
    <div class="font-bold px-4 pt-4 pb-1 border-b bg-red-700">
      {{ title }}
    </div>

    <div class="p-4">
      <div class="flex flex-col gap-2">
        <div
          v-for="(item, index) in items"
          :key="index"
        >
          {{ item }}
        </div>
      </div>
    </div>
  </div>
</template>