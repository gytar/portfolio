<template>
  <header>
    <nav>
      <router-link to="/">Accueil</router-link>
      <router-link to="/about">A propos</router-link>
      <router-link to="/route">Parcours</router-link>
      <router-link to="/projects">Projets</router-link>
      <router-link to="/contact">Contact</router-link>
    </nav>
  </header>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
export default {
  RouterLink,
  RouterView,
};
</script>

<style scoped>
header {
  max-height: 100vh;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

nav {
  display: flex;
  transform: translateX(50%);
  justify-content: center;
  align-items: center;
  top: -2rem;
  font-size: 12px;
  text-align: center;
  padding: 3em;
  width: 50vw;
}

nav a.router-link-exact-active {
  color: var(--white);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
