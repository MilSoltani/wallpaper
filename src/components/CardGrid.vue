<script setup>
import { ref } from 'vue'
import Card from './Card.vue'

const cards = ref(
  Array.from({ length: 25 }, (_, index) => ({
    id: index + 1,
    title: `header ${index + 1}`,
    items: [
      'test 1',
      'test 2',
      'test 3',
      'test 4',
      'test 5'
    ]
  }))
)
</script>

<template>
  <div class="grid grid-cols-5 gap-10 m-20 text-white">
    <Card
      v-for="card in cards"
      :key="card.id"
      :title="card.title"
      :items="card.items"
    />
  </div>
</template>