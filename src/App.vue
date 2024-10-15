<script>
import { RouterView } from 'vue-router'
import NavbarComponent from './components/NavbarComponent.vue';

export default {
  components: {
    NavbarComponent,
    RouterView,
  },
};
</script>

<template>
  <header>
    <h1>Marven Cantave's Portfolio</h1>
    <NavbarComponent />
  </header>
  <router-view v-slot="{Component}">
  <transition name="fade" mode="out-in">
    <component :is="Component" />
  </transition>
  </router-view>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
  display: flex;
  justify-content: space-between;
  background-color: white;
  padding: 20px;
  margin: 0px;
  font-family: 'Oswald', sans-serif;
  border-radius: 8px;

}

main {
  padding: 30px;
  background-color: whitesmoke;
}

nav {
  margin-top: 10px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
