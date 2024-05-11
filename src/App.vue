<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Home from './components/Home.vue'
import Accordeon from './components/Accordion.vue'
import { ref } from 'vue'

const events = ref([
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  },
  {
    title: 'Hawaiian party',
    img: '../src/assets/IMG_96781.png',
    date: '2023-12-02'
  }
])
</script>

<template>
  <div class="home__section">
    <Header />
    <Home />
    <Footer />
  </div>
  <div class="events__section">
    <Accordeon v-bind:items="events" />
  </div>
</template>

<style scoped>
.home__section {
  min-height: 100vh;
  display: grid;
  grid-template-rows: auto 1fr auto;
}
.events__section {
  padding: 5vw;
}
</style>
