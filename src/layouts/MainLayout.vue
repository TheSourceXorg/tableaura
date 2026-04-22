<template>
  <q-layout view="lHr lpR lFf">

    <!-- Header -->
    <q-header
      overlay
      :class="['table-aura-header', headerClass]"
      :elevated="false"
    >
      <q-toolbar class="header-toolbar container">

        <!-- Logo -->
        <div class="logo">
          <span class="logo-table">TABLE</span>
          <span class="logo-aura">AURA</span>
        </div>

        <q-space />

        <!-- Nav Links (desktop) -->
        <nav class="nav-links gt-sm">
          <router-link
            v-for="link in navLinks"
            :key="link.name"
            :to="link.path"
            class="nav-link"
            active-class="nav-link--active"
          >
            {{ link.name }}
          </router-link>
        </nav>

        <!-- Mobile menu button -->
        <q-btn
          flat
          dense
          round
          icon="menu"
          class="lt-md text-white"
          @click="drawer = !drawer"
        />

      </q-toolbar>
    </q-header>

    <!-- Mobile Drawer -->
    <q-drawer v-model="drawer" side="right" overlay class="mobile-drawer">
      <div class="drawer-content">
        <div class="logo q-pa-md">
          <span class="logo-table">TABLE</span>
          <span class="logo-aura">AURA</span>
        </div>
        <q-list>
          <q-item
            v-for="link in navLinks"
            :key="link.name"
            clickable
            :to="link.path"
            class="drawer-item"
            active-class="drawer-item--active"
            @click="drawer = false"
          >
            <q-item-section>{{ link.name }}</q-item-section>
          </q-item>
        </q-list>
      </div>
    </q-drawer>

    <!-- Page Content -->
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Footer -->
    <div class="table-aura-footer">
      <div class="footer-inner">

        <!-- Brand -->
        <div class="footer-brand">
          <div class="logo footer-logo">
            <span class="logo-table">TABLE</span>
            <span class="logo-aura">AURA</span>
          </div>
          <p class="footer-tagline">
            Experience the art of fine dining with our<br />
            carefully crafted dishes and elegant atmosphere.
          </p>
        </div>

        <!-- Quick Links -->
        <div class="footer-section">
          <h6 class="footer-heading">QUICK LINKS</h6>
          <ul class="footer-list">
            <li><router-link to="/menu" class="footer-link">Menu</router-link></li>
            <li><router-link to="/about" class="footer-link">About Us</router-link></li>
            <li><router-link to="/reservation" class="footer-link">Reservations</router-link></li>
            <li><router-link to="/contact" class="footer-link">Contact</router-link></li>
          </ul>
        </div>

        <!-- Contact -->
        <div class="footer-section">
          <h6 class="footer-heading">CONTACT</h6>
          <ul class="footer-list contact-list">
            <li>
              <q-icon name="place" class="contact-icon" />
              <span>123 Culinary Street, NY 10001</span>
            </li>
            <li>
              <q-icon name="phone" class="contact-icon" />
              <span>(555) 123-4567</span>
            </li>
            <li>
              <q-icon name="mail" class="contact-icon" />
              <span>info@tableaura.com</span>
            </li>
          </ul>
        </div>

        <!-- Follow Us -->
        <div class="footer-section">
          <h6 class="footer-heading">FOLLOW US</h6>
          <div class="social-links">
            <a href="#" class="social-btn" aria-label="Instagram">
              <q-icon name="fab fa-instagram" />
            </a>
            <a href="#" class="social-btn" aria-label="Facebook">
              <q-icon name="fab fa-facebook-f" />
            </a>
            <a href="#" class="social-btn" aria-label="Twitter">
              <q-icon name="fab fa-twitter" />
            </a>
          </div>
        </div>

      </div>

      <div class="footer-bottom">
        <span>© {{ new Date().getFullYear() }} Table Aura. All rights reserved.</span>
      </div>
    </div>

    <!-- Cursor Ring -->
    <div class="cursor-ring" :style="ringStyle()" />

  </q-layout>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const drawer = ref(false)
const scrolled = ref(false)


const navLinks = [
  { name: 'HOME', path: '/' },
  { name: 'MENU', path: '/menu' },
  { name: 'ABOUT', path: '/about' },
  { name: 'GALLERY', path: '/gallery' },
  { name: 'RESERVATION', path: '/reservation' },
  { name: 'CONTACT', path: '/contact' },
]

// Header class: transparent only on home + not scrolled
const isHomePage = computed(() => route.path === '/')

const headerClass = computed(() => {
  if (isHomePage.value && !scrolled.value) {
    return 'header--transparent'
  }
  return 'header--solid'
})

const handleScroll = () => {
  scrolled.value = window.scrollY > 60
}

// ── Cursor ──────────────────────────────────────────
const x = ref(0)
const y = ref(0)
const targetX = ref(0)
const targetY = ref(0)

const handleMouseMove = (e) => {
  targetX.value = e.clientX
  targetY.value = e.clientY
}

const animate = () => {
  const speed = 0.1
  x.value += (targetX.value - x.value) * speed
  y.value += (targetY.value - y.value) * speed
  requestAnimationFrame(animate)
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
  window.addEventListener('scroll', handleScroll, { passive: true })
  animate()
})

onBeforeUnmount(() => {
  window.removeEventListener('mousemove', handleMouseMove)
  window.removeEventListener('scroll', handleScroll)
})

const size = 25
const ringStyle = () => ({
  transform: `translate3d(${x.value - size / 2}px, ${y.value - size / 2}px, 0)`
})
</script>
