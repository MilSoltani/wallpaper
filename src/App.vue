<script setup>
import { ref } from 'vue'
import domtoimage from 'dom-to-image'
import CardGrid from './components/CardGrid.vue'

const mainRef = ref(null)

const capturePage = async () => {
  const node = mainRef.value
  const button = node.querySelector('button')
  const originalOverflow = node.style.overflow
  const originalButtonVisibility = button.style.visibility
  
  node.style.overflow = 'visible'
  button.style.visibility = 'hidden'

  try {
    const dataUrl = await domtoimage.toPng(node, {
      quality: 1.0,
      width: 3840,
      height: 2160,
      style: {
        'transform': 'none',
        'overflow': 'visible',
      },
    })
    const link = document.createElement('a')
    link.download = 'wallpaper.png'
    link.href = dataUrl
    link.click()
  } catch (error) {
    console.error('Error capturing page:', error)
  } finally {
    node.style.overflow = originalOverflow
    button.style.visibility = originalButtonVisibility
  }
}
</script>

<template>
  <main
    ref="mainRef"
    class="w-[3840px] h-[2160px] overflow-hidden bg-gray-900 box-border p-20 font-mono text-4xl"
  >
    <CardGrid />
    <button
      @click="capturePage"
      class="fixed bottom-4 right-4 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded cursor-pointer"
    >
      Download as PNG
    </button>
  </main>
</template>