<script>
import { RouterLink, RouterView } from "vue-router";
export default {
  RouterLink,
  RouterView,
};
</script>
<template>
  <section class="not-found-section">
    <div class="not-found">
      <h3>Oh nooon !</h3>
      <img src="@/assets/images/robot.webp" alt="robot not found" />
      <h1>Page non trouvée</h1>
      <div class="home-btn">
        <router-link class="link" :to="{ name: 'home' }">Accueil</router-link>
      </div>
    </div>
  </section>
</template>

<style>
.not-found-section {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.not-found {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  height: 100%;
}
.not-found img {
  width: 15em;
}
.home-btn {
  background-color: var(--pink);
  color: var(--white);
  padding: 1em 2em;
  border-radius: 0.5em;
  cursor: pointer;
}
.home-button .link {
  color: var(--white);
  text-decoration: none;
}
</style>
