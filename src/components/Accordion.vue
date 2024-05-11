<script setup>
import { ref } from 'vue'

const items = defineProps(['items'])
const activeIndex = ref(0)

const toggleAccordion = (index) => {
  activeIndex.value = activeIndex.value === index ? null : index
}
</script>

<template>
  <h2>All events</h2>
  <div class="accordion__container">
    <div
      v-for="(item, index) in items.items"
      :key="index"
      class="accordion__item"
      :class="{ active: activeIndex === index }"
      @click="toggleAccordion(index)"
    >
      <div class="accordion__header">
        <span class="accordion__header-text">
          {{ item.title }}
        </span>
        <div class="accordion__header-index">{{ String(index + 1).padStart(2, '0') }}</div>
      </div>
      <div
        v-if="activeIndex === index"
        class="accordion__content"
        :style="{ 'background-image': `url(${item.img})` }"
      >
        <div class="accordion__content-block">
          <p class="index-content-block">{{ String(index + 1).padStart(2, '0') }}</p>
          <div>
            <h4 class="accordion__content-title">{{ item.title }}</h4>
            <p class="accordion__content-date">{{ item.date }}</p>
            <button class="accordion__content-button">More information</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400');

.index-content-block {
  position: relative;
  right: 65px;
  font-size: 14vw;
  color: #ffffff21;
  font-weight: 700;
}
.accordion__container {
  display: flex;
  justify-content: center;
  gap: 1px;
  height: calc(var(--index) * 22);
  width: 80vh;
  margin: 2vh auto;
}
.accordion__content-date {
  color: var(--color-white);
  margin-left: 10px;
}

.accordion__item {
  cursor: pointer;
  display: flex;
  background-size: cover;
}
.accordion__content-title {
  font-size: 1.5vw;
  margin: 2vw 10px 0;
}

.accordion__content-title,
.accordion__content-button {
  font-family: 'Poppins', sans-serif;
  font-weight: 400;
}
.accordion__content-button {
  background-color: transparent;
  border-width: 1px 1px 1px 3px;
  border-style: solid;
  border-color: var(--color-white);
  color: var(--color-white);
  padding: 10px;
  font-size: 1vw;
  margin: 2vw 10px;
  cursor: pointer;
}
.accordion__content-button:hover {
  background-color: #ffffff20;
}
.accordion__header {
  background-image: linear-gradient(#000, var(--color-blue));
  color: var(--color-white);
  width: 4vw;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: flex-end;
  font-family: 'Poppins', sans-serif;
  font-weight: 400;
  font-size: 1.4vw;
}
.accordion__header:hover {
  background-image: linear-gradient(#000, #161e42);
}

.accordion__header-text {
  white-space: nowrap;
  width: 0%;
  margin: 0;
  transform: rotate(-90deg);
}

.accordion__content-block {
  width: 40%;
  color: var(--color-white);
  height: 100%;
  background-color: rgb(0 0 0 / 85%);
  backdrop-filter: blur(5px);
  overflow: hidden;
}

.active .accordion__content {
  background-size: cover;
  width: 50vw;
}

.active .accordion__header {
  margin-right: 2px;
  background-color: var(--color-blue);
}
@media (max-width: 768px) {
  .accordion__header-index {
    font-size: 4vw;
    padding: 0 10px;
  }
  .accordion__container {
    height: auto;
    width: 80vw;
    flex-direction: column;
  }
  .accordion__item[data-v-8aecb5f8] {
    display: flex;
    background-size: cover;
    flex-direction: column-reverse;
  }
  .accordion__header {
    font-size: 2vw;
    width: auto;
    flex-direction: row-reverse;
    padding: 10px;
    background-image: linear-gradient(to left, #000, var(--color-blue));
  }
  .active .accordion__header {
    margin: 0;
    justify-content: flex-end;
  }
  .accordion__header-text {
    transform: none;
    width: auto;
  }
  .active .accordion__content {
    width: 100%;
    height: 40vh;
    display: flex;
    align-items: flex-end;
  }
  .accordion__content-block {
    width: 100%;
    height: 40%;
    display: flex;
    flex-direction: row-reverse;
    justify-content: space-between;
  }
}
@media (max-width: 500px) {
  .accordion__container {
    width: 90vw;
  }
  .accordion__content-title {
    font-size: 5vw;
  }
  .accordion__content-button,
  .accordion__header {
    font-size: 3vw;
  }
  .index-content-block {
    right: -13px;
    font-size: 34vw;
  }
}
</style>
