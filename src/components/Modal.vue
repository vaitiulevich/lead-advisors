<script setup>
import { ref, defineProps } from 'vue'

const props = defineProps(['status', 'title', 'subtitle'])
const open = ref(props.status)
</script>

<template>
  <Teleport to="body">
    <div v-if="open" class="modal__mask">
      <div class="modal__wrapper">
        <div class="modal__container">
          <div class="modal__header">
            <slot name="header"
              ><img
                class="modal__header__close"
                @click="
                  () => {
                    $emit('close-modal')
                    open = false
                  }
                "
                src="../assets/close.svg"
            /></slot>
          </div>

          <div class="modal__body">
            <slot name="body">
              <h3 class="modal__body__title">{{ props.title }}</h3>
              <p class="modal__body__subtitle">
                {{ props.subtitle }}
              </p>
            </slot>
          </div>

          <div class="modal__footer">
            <slot name="footer">
              <button
                class="modal__footer__close"
                @click="
                  () => {
                    $emit('close-modal')
                    open = false
                  }
                "
              >
                Close
              </button>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
.modal__footer__close {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 12vw;
  padding: 18px;
  background-color: var(--color-blue);
  border: none;
  border-radius: 40px;
  color: var(--color-white);
  font-size: 1.2vw;
  font-weight: 300;
  flex-wrap: nowrap;
}
.modal__footer {
  display: flex;
  justify-content: center;
}
.modal__body__subtitle {
  text-align: center;
  font-size: 16px;
}

.modal__header__close,
.modal__footer__close {
  cursor: pointer;
}
.modal__mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #162c4e91;
  display: table;
  transition: opacity 0.3s ease;
}

.modal__wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal__container {
  height: 35vh;
  width: 270px;
  margin: 0px auto;
  padding: 20px;
  background-color: var(--color-white);
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal__header {
  text-align: end;
}

.modal__body {
  margin: 20px 0;
}

.modal__footer__close {
  float: right;
}
</style>
