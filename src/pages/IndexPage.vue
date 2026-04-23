<template>
  <q-page>

    <!-- HERO SECTION -->
    <div class="hero">
      <div class="hero-content">
        <div class="fs-70 text-weight-bold" style="line-height: 0.9;">Where Culinary Art <br> <span class="fs-70 text-weight-bold text-primary">Meets Excellence</span></div>
        <div class="fs-18 q-mt-lg text-grey-4">Experience the finest flavors crafted by world-class chefs in an atmosphere <br> of unparalleled elegance</div>
        <div class="hero-buttons">
          <q-btn
            class="btn primary-btn"
            no-caps
            unelevated
          >
            View Menu
            <q-icon name="arrow_forward_ios" size="xs" class="q-ml-sm icon" />
          </q-btn>

          <q-btn
            class="btn outline-btn"
            no-caps
            unelevated
          >
            Book a Table
          </q-btn>
        </div>
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
      rgb(0, 0, 0) 0%,
      rgba(0, 0, 0, 0.637) 40%,
      rgba(0, 0, 0, 0.582) 50%,
      rgba(0, 0, 0, 0.637) 65%,
      rgb(0, 0, 0) 100%
    ),
    url('https://images.unsplash.com/photo-1414235077428-338989a2e8c0')
      center/cover no-repeat;

  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-align: center;
}

/* TITLE */
.hero-title {
  line-height: 0.9;
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

/* BUTTON CONTAINER */
.hero-buttons {
  margin-top: 30px;
  display: flex;
  gap: 20px;
  justify-content: center;
}

/* COMMON BUTTON STYLE (works with q-btn) */
.btn {
  padding: 14px 28px;
  font-size: 16px;
  border-radius: 40px;
  cursor: pointer;
  border: none;

  transition:
    transform 0.25s cubic-bezier(0.4, 0, 0.2, 1),
    background-color 0.25s ease,
    color 0.25s ease,
    box-shadow 0.25s ease;

  transform: translateZ(0);
  will-change: transform;
}

/* PRIMARY BUTTON */
.primary-btn {
  background: #f5a623;
  color: black;
}

.primary-btn:hover {
  background: #ffbf47;
  transform: scale(1.05);
  box-shadow: 0 10px 25px rgba(245, 166, 35, 0.4);
}

/* OUTLINE BUTTON */
.outline-btn {
  background: transparent;
  border: 2px solid white;
  color: white;
}

.outline-btn:hover {
  background: white;
  color: black;
  transform: scale(1.05);
  box-shadow: 0 10px 25px rgba(255, 255, 255, 0.2);
}

/* CLICK EFFECT */
.btn:active {
  transform: scale(0.97);
}

/* ICON ANIMATION */
.icon {
  display: inline-block;
  transition: transform 0.25s ease;
}

.primary-btn:hover .icon {
  transform: translateX(6px);
}
</style>