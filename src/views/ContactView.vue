<script setup>
import HeaderItem from '@/components/HeaderItem.vue';
</script>

<template>
  <section class="contact">
    <header-item>
      <template #title>Contact</template>
    </header-item>
    <div class="contact-links">
      <a href="https://github.com/gytar" target="_blank" rel="noopener">
        <img src="@/assets/images/github.webp" alt="github" />
      </a>
      <a
        href="https://www.linkedin.com/in/guillaume-perrot-clermont/"
        target="_blank"
        rel="noopener"
      >
        <img src="@/assets/images/linkedin.webp" alt="linkedin" />
      </a>
    </div>

    <a href="#">
      <div class="download-resume">
        <span>Mon CV</span>
        <i class="bi bi-download"></i>
      </div>
    </a>
  </section>
</template>

<style>
@media (min-width: 1024px) {
  .contact {
  }
}

.contact {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: space-evenly;
  background-color: var(--white);
  height: 80vh;
  box-shadow: rgb(29, 29, 29) 0px 0px 10px;
  border-radius: 10px;

}
.contact h1 {
  color: var(--black);
  font-size: 2.5rem;
}

.contact-links img {
  width: 5rem;
  margin: 1rem;
}

.contact-link a {
  text-decoration: none;
}

.download-resume {
  display: flex;
  align-items: center;
  justify-content: space-around;
  width: 17rem;
  border: var(--pink) solid 3px;
  border-radius: 10px;
  padding: 0.7em 0.5em;
  color: var(--pink);
  font-size: 1.5em;
  font-family: var(--rubik);
}
</style>
