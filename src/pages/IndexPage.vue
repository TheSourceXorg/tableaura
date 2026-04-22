<template>
  <q-page>

    <!-- HERO SECTION -->
    <div class="hero">
      <div class="hero-content">
        <h1>TABLE AURA</h1>
        <p>Luxury Dining Experience</p>
      </div>
    </div>

    <!-- SCROLL CONTENT -->
    <div class="content">
      <div class="section" v-for="i in 5" :key="i">
        <h2>Section {{ i }}</h2>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit.
          Quasi, doloremque! This is just dummy content to test scrolling.
        </p>
      </div>
    </div>

  </q-page>
</template>

<script setup>
</script>

<style scoped>

/* HERO */
.hero {
  height: 100vh;

  background:
    linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0.87) 0%,     /* top black */
      rgba(0, 0, 0, 0.377) 40%,    /* fade */
      rgba(0, 0, 0, 0.0) 50%,    /* transparent middle */
      rgba(0, 0, 0, 0.37) 65%,    /* start dark again */
      rgba(0, 0, 0, 0.9) 100%    /* bottom black */
    ),
    url('https://images.unsplash.com/photo-1414235077428-338989a2e8c0')
      center/cover no-repeat;

  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-align: center;
}

.hero-content h1 {
  font-size: 3rem;
  letter-spacing: 0.2em;
}

.hero-content p {
  font-size: 1.2rem;
  opacity: 0.8;
}

/* CONTENT BELOW */
.content {
  background: #0a0a0a;
}

.section {
  max-width: 800px;
  margin: 0 auto 60px;
  color: #ccc;
}

.section h2 {
  color: white;
  margin-bottom: 10px;
}

</style>