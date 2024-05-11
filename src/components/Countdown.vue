<script setup>
import { ref, onMounted } from 'vue'

const targetDate = new Date('2024-07-24T00:00:00').getTime()
const currentDate = ref(new Date().getTime())
const showMobileMarker = window.matchMedia('(max-width:800px)').matches

const isEnded = ref(false)

const days = ref(0)
const hours = ref(0)
const minutes = ref(0)
const seconds = ref(0)

const calculateTimeRemaining = () => {
  const difference = targetDate - currentDate.value

  if (difference < 0) {
    isEnded.value = true
    return
  }
  days.value = Math.floor(difference / (1000 * 60 * 60 * 24))
  hours.value = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  minutes.value = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60))
  seconds.value = Math.floor((difference % (1000 * 60)) / 1000)
}

const startCountdown = () => {
  let timer = setInterval(() => {
    currentDate.value = new Date().getTime()
    calculateTimeRemaining()

    if (currentDate.value >= targetDate) {
      clearInterval(timer)
      isEnded.value = true
    }
  }, 1000)
}

onMounted(() => {
  calculateTimeRemaining()
  startCountdown()
})
</script>

<template>
  <div class="hero__countdown">
    <div v-if="isEnded">Timer ended.</div>
    <div v-if="!isEnded" class="hero__countdown__time">
      <div class="countdown__time__marker">
        <span class="countdown__time">{{ String(days).padStart(2, '0') }}</span>
        <img class="time__marker__field" src="../assets/marker-field.svg" />
        <span class="time__marker">{{ showMobileMarker ? 'DD' : 'Days' }}</span>
      </div>
      <span class="countdown__time__twopoints">:</span>
      <div class="countdown__time__marker">
        <span class="countdown__time">{{ String(hours).padStart(2, '0') }}</span>
        <img class="time__marker__field" src="../assets/marker-field.svg" />
        <span class="time__marker">{{ showMobileMarker ? 'HH' : 'Hours' }}</span>
      </div>
      <span class="countdown__time__twopoints">:</span>
      <div class="countdown__time__marker">
        <span class="countdown__time">{{ String(minutes).padStart(2, '0') }}</span>
        <img class="time__marker__field" src="../assets/marker-field.svg" />
        <span class="time__marker">{{ showMobileMarker ? 'MM' : 'Minutes' }}</span>
      </div>
      <span class="countdown__time__twopoints">:</span>
      <div class="countdown__time__marker">
        <span class="countdown__time">{{ String(seconds).padStart(2, '0') }}</span>
        <img class="time__marker__field" src="../assets/marker-field.svg" />
        <span class="time__marker">{{ showMobileMarker ? 'SS' : 'Seconds' }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600;300');

.hero__countdown {
  text-align: center;
  margin: 2vh 0 0;
}
.time__marker {
  position: relative;
  bottom: 40px;
  color: var(--color-white);
  font-weight: 300;
}
.countdown__time__marker {
  display: flex;
  flex-direction: column;
}
.countdown__time__twopoints,
.countdown__time {
  font-family: 'Poppins', sans-serif;
  font-weight: 600;
  margin: 0;
  color: var(--color-blue);
}
.countdown__time__twopoints {
  padding: 0 0.4vw;
}
.countdown__time,
.countdown__time__twopoints {
  font-size: calc(var(--index) * 3);
  line-height: 9vh;
}
.hero__countdown__time {
  width: 60vw;
  display: flex;
  justify-content: center;
}
.time__marker__field {
  width: calc(var(--index) * 5);
}
@media (max-width: 800px) {
  .time__marker {
    bottom: 3.5vh;
  }
  .time__marker__field {
    transform: scaleY(1.3);
  }
}
@media (max-width: 500px) {
  .time__marker__field {
    width: 20vw;
    transform: scaleY(1.5);
  }
  .hero__countdown {
    margin: 0;
  }
  .time__marker {
    bottom: 7vw;
    font-size: 4vw;
  }
}
</style>
