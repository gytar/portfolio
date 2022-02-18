<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import "animate.css";
</script>

<template class="welcome">
  <WelcomeItem>
    <template #title>Guillaume Perrot</template>
    <template #subtitle>Concepteur développeur d'applications</template>
  </WelcomeItem>
</template>

<style scoped>
@import "@/assets/base.css";
</style>
