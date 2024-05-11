<script setup>
import Modal from './Modal.vue'
import axios from 'axios'
import { ref } from 'vue'

const isShowModel = ref(false)
const email = ref(null)
const isntValid = ref(false)

const modalTitle = ref('')
const modalSubtitle = ref('')

const submitEmail = () => {
  validateEmail()
  if (isntValid.value) {
    return
  }
  axios
    .post('http://localhost:3000/emails', { email: email.value })
    .then((response) => {
      modalTitle.value = 'SUCCESS!'
      modalSubtitle.value = 'You have successfully subscribed to the email newsletter'
      isShowModel.value = true
      email.value = null
    })
    .catch((error) => {
      modalTitle.value = 'ERROR!'
      modalSubtitle.value = 'Something went wrong'
      isShowModel.value = true
      console.error(error)
    })
}
const validateEmail = () => {
  if (email.value === null) {
    isntValid.value = true
    return
  }

  if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email.value)) {
    isntValid.value = false
  } else {
    isntValid.value = true
  }
}
</script>

<template>
  <footer class="footer">
    <div>
      <div class="footer__setemail__block">
        <input
          class="setemail__block__input"
          v-model.trim="email"
          @change="validateEmail"
          placeholder="Enter your Email and get notified"
        />
        <button @click="submitEmail" class="setemail__block__button">
          <img alt="submit" src="../assets/submit-arrow.svg" />
        </button>
      </div>
      <Modal
        v-if="isShowModel"
        @close-modal="() => (isShowModel = false)"
        v-bind:status="isShowModel"
        v-bind:title="modalTitle"
        v-bind:subtitle="modalSubtitle"
      />
      <p class="err__email__input" v-if="isntValid">Please enter a valid email address</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  min-height: 200px;
  margin: 4vh 0 0;
  background-color: var(--color-blue);
  display: flex;
  align-items: center;
  justify-content: center;
}
.footer__events__link {
  color: var(--color-white);
  text-decoration: none;
  display: flex;
  align-items: center;
}
.footer__setemail__block {
  width: calc(var(--index) * 15);
  background-color: var(--color-white);
  padding: 10px;
  border-radius: 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.err__email__input {
  color: var(--color-red);
  margin: 0 25px;
  font-size: 1vw;
}
.setemail__block__input {
  width: 90%;
  outline: none;
  font-size: calc(var(--index) * 0.8);
  border: none;
}
.setemail__block__button {
  border: none;
  background-color: var(--color-red);
  display: flex;
  align-items: center;
  justify-content: center;
  height: 40px;
  width: 40px;
  border-radius: 50%;
  cursor: pointer;
}
@media (max-width: 500px) {
  .footer__setemail__block {
    width: 80vw;
  }
  .setemail__block__input {
    font-size: calc(var(--index) * 1.2);
  }
  .err__email__input {
    font-size: 4vw;
  }
}
</style>
