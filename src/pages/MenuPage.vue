<template>
  <q-page class="menu-page">

    <!-- Title -->
    <div class="text-center q-mt-xl">
      <h2 class="title">
        Our <span class="highlight">Menu</span>
      </h2>
      <p class="subtitle">
        A carefully curated selection of dishes prepared with the finest ingredients
      </p>
    </div>

    <!-- Tabs -->
    <div class="tabs q-mt-lg">
      <q-btn
        v-for="tab in tabs"
        :key="tab"
        :label="tab"
        :class="['tab-btn', activeTab === tab ? 'active' : '']"
        @click="activeTab = tab"
        unelevated
      />
    </div>

    <!-- Cards -->
    <div class="row q-col-gutter-lg q-mt-xl justify-center container">
      <div
        class="col-12 col-sm-6 col-md-3"
        v-for="item in menuItems"
        :key="item.name"
      >
        <q-card class="menu-card">

          <q-img :src="item.image" height="200px" />

          <q-card-section>
            <div class="row justify-between items-center">
              <div class="item-title">{{ item.name }}</div>
              <div class="price">${{ item.price }}</div>
            </div>

            <div class="desc">
              {{ item.desc }}
            </div>
          </q-card-section>

        </q-card>
      </div>
    </div>

  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const tabs = ['STARTERS', 'MAIN COURSE', 'DESSERTS', 'DRINKS']
const activeTab = ref('STARTERS')

const menuItems = [
  {
    name: 'Garden Fresh Salad',
    price: 18,
    desc: 'Organic greens with heirloom tomatoes, burrata, and balsamic reduction',
    image: 'https://images.unsplash.com/photo-1546793665-c74683f339c1',
    category:'starter'
  },
  {
    name: 'Seared Scallops',
    price: 28,
    desc: 'Pan-seared scallops with cauliflower purée and microgreens',
    image: 'https://images.unsplash.com/photo-1504674900247-0877df9cc836'
  },
  {
    name: 'Premium Sushi Selection',
    price: 35,
    desc: 'Chef’s selection of fresh sashimi and nigiri',
    image: 'https://images.unsplash.com/photo-1553621042-f6e147245754'
  },
  {
    name: 'Foie Gras Terrine',
    price: 32,
    desc: 'House-made foie gras with fig compote and toasted brioche',
    image: 'https://images.unsplash.com/photo-1551218808-94e220e084d2'
  }
]
</script>

<style scoped>
.menu-page {
  background: #0b0b0b;
  color: white;
  min-height: 100vh;
  padding-bottom: 50px;
}

/* Title */
.title {
  font-size: 42px;
  font-weight: bold;
}

.highlight {
  color: #ffa726;
}

.subtitle {
  color: #9aa0a6;
  margin-top: 10px;
}

/* Tabs */
.tabs {
  display: flex;
  justify-content: center;
  gap: 15px;
}

.tab-btn {
  background: #1c1c1c;
  color: #ccc;
  border-radius: 25px;
  padding: 10px 20px;
}

.tab-btn.active {
  background: #ffa726;
  color: black;
  box-shadow: 0 0 15px rgba(255, 167, 38, 0.7);
}

/* Cards */
.menu-card {
  background: #141414;
  border-radius: 16px;
  overflow: hidden;
  height:100%;
  transition: 0.3s;
}

.menu-card:hover {
  transform: translateY(-5px);
}

/* Text */
.item-title {
  font-size: 16px;
  font-weight: 600;
}

.price {
  color: #ffa726;
  font-weight: bold;
}

.desc {
  color: #9aa0a6;
  font-size: 13px;
  margin-top: 10px;
}
</style>
