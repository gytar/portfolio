<template>
  <header :class="{ 'scrolled-nav': scrollPosition }">
    <nav>
      <ul v-show="!mobile" class="navigation">
        <li>
          <router-link class="link" :to="{ name: 'home' }">Accueil</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: 'about' }"
            >A propos</router-link
          >
        </li>
        <li>
          <router-link class="link" :to="{ name: 'route' }"
            >Parcours</router-link
          >
        </li>
        <li>
          <router-link class="link" :to="{ name: 'projects' }"
            >Projets</router-link
          >
        </li>
        <li>
          <router-link class="link" :to="{ name: 'contact' }"
            >Contact</router-link
          >
        </li>
      </ul>
      <div class="icon">
        <i
          @click="toggleMobileNav"
          v-show="mobile"
          class="bi bi-list"
          :class="{ 'icon-active': mobileNav }"
        ></i>
      </div>
      <transition name="mobile-nav" appear>
        <ul v-show="mobileNav" class="dropdown-nav">
          <li><router-link @click="toggleMobileNav" class="link" :to="{ name: 'home' }">Accueil</router-link></li>
          <li><router-link @click="toggleMobileNav" class="link" :to="{ name: 'about' }">A propos</router-link></li>
          <li><router-link @click="toggleMobileNav" class="link" :to="{ name: 'route' }">Parcours</router-link ></li>
          <li><router-link @click="toggleMobileNav" class="link" :to="{ name: 'projects' }">Projets</router-link></li>
          <li><router-link @click="toggleMobileNav" class="link" :to="{ name: 'contact' }">Contact</router-link></li>
        </ul>
      </transition>
    </nav>
  </header>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
export default {
  RouterLink,
  RouterView,
  data() {
    return {
      scrollPosition: null,
      mobile: null,
      mobileNav: false,
      windowWidth: null,
    };
  },
  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
  },
  methods: {
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
    },
    checkScreen() {
      this.windowWidth = window.innerWidth;
      if (this.windowWidth < 820) {
        this.mobile = true;
      } else {
        this.mobile = false;
        this.mobileNav = false;
      }
    },
  },
};
</script>

<style scoped>
header {
  height: 10vh;
  z-index: 99;
  min-width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  transition: 0.5s ease all;
  background-color: var(--black-soft);
}

header nav {
  position: relative;
  display: flex;
  flex-direction: row;
  padding: 1em 0;
  transition: 0.5s ease all;
  min-width: 100%; /* Fix for mobile */
  min-height: 100%;
}

@media (min-width: 60em) {
  header nav {
    max-width: 60em;
  }
  header {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
header nav .navigation {
  min-height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;
}
header nav ul li {
  list-style: none;
  text-decoration: none;
  color: var(--white);
  transition: 0.5s ease all;
  padding-bottom: 4px;
  border-bottom: 1px solid transparent;
  margin: 1em 1em;
}
header nav ul li .link {
  text-decoration: none;
  color: var(--white);
  transition: 0.5s ease all;
}
header nav ul li:hover {
  color: var(--pink);
  border-color: var(--pink);
}
header nav .icon {
  display: flex;
  align-items: center;
  position: absolute;
  top: 0;
  right: 2vw;
  height: 100%;
}

header nav .icon-active {
  transform: rotate(180deg);
}
header nav .icon i {
  font-size: 2em;
  color: var(--white);
  cursor: pointer;
  transition: 0.8s ease all;
  z-index: 99;
}

header nav .dropdown-nav {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  background-color: var(--light-blue);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 3em 2em;
  transition: 0.5s ease all;
}

header nav .dropdown-nav li {
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid var(--white);
  width: 100%;
  text-align: center;
  padding: 0;
  margin: 0;
  transition: 0.5s ease all;
}

header nav .dropdown-nav li .link:hover {
  background-color: var(--black-soft);
  color: var(--pink);
}
header nav .dropdown-nav li .link {
  color: var(--white);
  text-decoration: none;
  min-height: 100%;
  width: 100%;
  padding: 0.5em 0;
}

header nav .navigation li a.router-link-exact-active {
  color: var(--pink);
}

header nav .dropdown-nav li a.router-link-exact-active {
  color: var(--pink);
  background-color: var(--black-soft);
}
.mobile-nav-leave-to,
.mobile-nav-enter-from {
  transform: translateY(-30rem);
}

.mobile-nav-enter-active,
.mobile-nav-leave-active {
  transition: all 0.5s ease-in-out;
}
</style>
