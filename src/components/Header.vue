<script></script>

<template>
  <header>
    <transition name="fade" appear>
      <img alt="left" class="header__vector__left" src="../assets/VectorLeft.svg" />
    </transition>
    <transition name="fade" appear>
      <img alt="Lead advisors logo" class="header__vector__right" src="../assets/VectorRight.svg" />
    </transition>
    <transition name="fade-logo" appear>
      <img alt="Lead advisors logo" class="header__logo" src="../assets/logo.svg" />
    </transition>
  </header>
</template>

<style scoped>
.fade-logo-enter-active {
  animation: fade-logo-in 1s;
}
.fade-logo-leave-active {
  animation: fade-logo-in 1s;
}
@keyframes fade-logo-in {
  0% {
    transform: translateY(-30px);
    opacity: 0;
  }
  100% {
    transform: translateY(0px);
    opacity: 1;
  }
}
.fade-enter-active {
  animation: bounce-in 1s;
}
.fade-leave-active {
  animation: bounce-in 1s;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}
header {
  text-align: center;
  padding-top: 60px;
  z-index: 1;
}
.header__logo {
  height: 60px;
  cursor: pointer;
}
.header__vector__left {
  width: calc(var(--index) * 32);
  position: absolute;
  top: calc(var(--index) * -13);
  left: calc(var(--index) * -15);
  z-index: 0;
}
.header__vector__right {
  width: calc(var(--index) * 30);
  position: absolute;
  top: calc(var(--index) * -22);
  right: calc(var(--index) * -17);
  z-index: 0;
}
</style>
