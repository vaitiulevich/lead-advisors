<script setup>
import Countdown from './Countdown.vue'
</script>

<template>
  <div class="hero">
    <div class="hero__title">
      <h2 class="hero__tittle__text">Under Construction</h2>
      <p class="hero__subtitle">We're making lots of improvements and will be back soon</p>
    </div>
    <Countdown />
    <div class="hero__toevent__block">
      <p class="hero__toevent__text">Check our event page when you wait:</p>
      <a href="https://www.events/events" class="hero__toevent__button">
        <span>Go to the event</span> <img src="../assets/to-right-arrow.svg" alt="to events" />
      </a>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600');

.hero__toevent__button {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px;
  background-color: var(--color-blue);
  border: none;
  border-radius: 40px;
  color: white;
  flex-wrap: nowrap;
  margin-top: 2vh;
  cursor: pointer;
}
.hero__toevent__button span {
  white-space: nowrap;
  margin-right: 4vw;
}
.hero__toevent__block {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 2vh 0 0;
}

.hero {
  margin-top: 70px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.hero__title {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.hero__subtitle {
  width: calc(var(--index) * 20);
}
.hero__subtitle {
  margin: 0;
  text-align: center;
}
@media (max-width: 500px) {
  .hero__tittle__text {
    font-size: 10vw;
  }
  .hero__subtitle {
    width: 95vw;
  }
  .hero__toevent__text {
    font-size: 5vw;
  }
  .hero__toevent__block {
    margin: 0;
  }
}
</style>
