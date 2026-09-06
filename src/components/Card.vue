<script setup>
defineProps({
  title: {
    type: String,
    default: 'header'
  },
  items: {
    type: Array,
    default: () => []
  },
  color: {
    type: String,
    default: 'red-700'
  }
})
</script>

<template>
  <div class="rounded-xl h-[430px] flex flex-col border-4" :class="`border-${color}`">
    <div class="font-bold px-4 pt-4 pb-1 border-b" :class="`bg-${color}`">
      {{ title }}
    </div>

    <div class="p-4">
      <div class="flex flex-col gap-2">
        <div
          v-for="(item, index) in items"
          :key="index"
        >
          <span class="text-white font-mono text-3xl">{{ item.cmd }}</span>
          <span class="text-gray-400 ms-8 text-3xl">{{ item.desc }}</span>
        </div>
      </div>
    </div>
  </div>
</template>