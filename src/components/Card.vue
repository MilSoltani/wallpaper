<script setup>
const props = defineProps({
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

const tailwindColors = {
  'rose-700': '#be185d',
  'fuchsia-600': '#c026d3',
  'lime-700': '#4d7c0f',
  'indigo-600': '#4f46e5',
  'amber-700': '#b45309',
  'teal-600': '#0d9488',
  'orange-600': '#ea580c',
  'cyan-700': '#0e7490',
  'purple-600': '#7c3aed',
  'emerald-700': '#047857',
  'sky-600': '#0284c7',
  'red-600': '#dc2626',
  'teal-700': '#0f766e',
  'green-600': '#16a34a',
  'violet-600': '#7c3aed',
  'pink-600': '#db2777',
  'blue-600': '#2563eb',
  'lime-600': '#65a30d',
  'orange-700': '#c2410c',
  'cyan-600': '#06b6d4',
  'rose-600': '#e11d48',
  'emerald-600': '#059669',
  'amber-600': '#d97706',
  'yellow-600': '#ca8a04',
}

const colorHex = tailwindColors[props.color] || '#dc2626'
</script>

<template>
  <div class="rounded-xl h-[430px] flex flex-col border-4" :style="{ borderColor: colorHex }">
    <div class="font-bold px-4 pt-4 pb-1 border-b" :style="{ backgroundColor: colorHex }">
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