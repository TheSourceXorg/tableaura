<template>
  <q-layout view="hHh lpR fFf">

    <!-- Header -->


  <q-layout view="hHh lpR fFf">

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>


    <!-- This is your original code (already added correctly) -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Cursor -->
    <div class="cursor-ring" :style="ringStyle()" />

  </q-layout>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

// current position (rendered)
const x = ref(0)
const y = ref(0)

// target (mouse)
const targetX = ref(0)
const targetY = ref(0)

// mouse tracking (GLOBAL)
const handleMouseMove = (e) => {
  targetX.value = e.clientX
  targetY.value = e.clientY
}

// animation loop (smooth delay)
const animate = () => {
  const speed = 0.1 // 0.05 = slow, 0.1 = balanced, 0.2 = tight

  x.value += (targetX.value - x.value) * speed
  y.value += (targetY.value - y.value) * speed

  requestAnimationFrame(animate)
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
  animate()
})

onBeforeUnmount(() => {
  window.removeEventListener('mousemove', handleMouseMove)
})

// exact centering (no percentage guesswork)
const size = 25

const ringStyle = () => ({
  transform: `translate3d(${x.value - size / 2}px, ${y.value - size / 2}px, 0)`
})
</script>

<style scoped>

.cursor-ring {
  position: fixed;
  top: 0;
  left: 0;

  width: 25px;
  height: 25px;
  background: rgba(255, 183, 28, 0.65);
  border-radius: 50%;

  pointer-events: none;
  z-index: 999999;

  will-change: transform;
}
</style>
