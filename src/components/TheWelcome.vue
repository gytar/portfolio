<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import "animate.css";
</script>

<template class="welcome">
  <section class="welcome-section">
    <WelcomeItem>
      <template #title>Guillaume Perrot</template>
      <template #subtitle>Concepteur développeur d'applications</template>
    </WelcomeItem>
  </section>
</template>

<style>
.welcome {
  margin-top: 10vh;
}
</style>
