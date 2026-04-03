<template>
  <q-layout view="hHh lpR fFf">
    <div @mousemove="onMouseMove" class="cursor-area">
      <!-- your page content -->
      <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
      <!-- <div class="cursor-dot" :style="dotStyle" /> -->
      <div class="cursor-ring" :style="ringStyle" />
    </div>
  </q-layout>
</template>

<script setup>
import { ref, computed } from 'vue'

const x = ref(0)
const y = ref(0)

const onMouseMove = (e) => {
  x.value = e.clientX
  y.value = e.clientY
}

// const dotStyle = computed(() => ({
//   left: x.value + 'px',
//   top: y.value + 'px',
// }))

const ringStyle = computed(() => ({
  left: x.value + 'px',
  top: y.value + 'px',
}))
</script>

<style scoped>
.cursor-area {
  position: relative;
  min-height: 100vh;
}

/* .cursor-dot {
  position: fixed;
  width: 10px;
  height: 10px;
  background: #000;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
  z-index: 9999;
  transition: transform 0.08s ease;
} */

.cursor-ring {
  position: fixed;
  width: 25px;
  height: 25px;
  background: rgba(255, 183, 28, 0.651);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
  z-index: 9998;
  transition: left 0.09s ease, top 0.09s ease;
}
</style>