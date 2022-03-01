<script setup>
import { RouterView } from "vue-router";
import NavigationItem from "@/components/NavigationItem.vue";
import "animate.css";
</script>

<template>
  <NavigationItem />

  <router-view ref="nestedView" v-slot="{ Component }">
    <Transition name="route" mode="out-in">
      <component :is="Component"></component>
    </Transition>
  </router-view>
</template>

<style>
@import "@/assets/base.css";

#app {
  width: 100vw;
  height: 100vh;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
  display: flex;
  flex-direction: column;
}

.route-enter-from {
  opacity: 0;
  transform: translateY(4rem);
}

.route-enter-active,
.route-leave-active {
  transition: all 0.4s ease;
}

.route-leave-to {
  opacity: 0;
  transform: translateY(-4rem);
}

section {
  margin-top: 10vh;
}
</style>
