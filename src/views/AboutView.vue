<script setup>
import HeaderItem from "@/components/HeaderItem.vue";
</script>
<template>
  <section class="about">
    <HeaderItem>
      <template #title>A propos</template>
    </HeaderItem>
    <div class="image-and-text">
      <div class="picture-frame"></div>
      <div class="pink-line"></div>
      <div class="text">
        <p>
          Bonjour, je suis Guillaume Perrot, concepteur et développeur
          d'application. Je suis passionné par le développement web et je suis
          actuellement en recherche d'emploi en France
        </p>

        <p>
          J'ai commencé l'infomatique en autodidacte, avec des vidéos YouTube,
          puis, en 2020, j'ai pris la résolution d'aller vers l'informatique.
        </p>

        <p>
          J'aime beaucoup conceptualiser des sites avec créativité, soin et
          rigueur. J'ai beaucoup codé avec PHP, Symfony, JavaScript, HTML&CSS,
          et Flutter pour le mobile
        </p>
      </div>
    </div>
  </section>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 85vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .image-and-text {
    flex-direction: row !important;
    width: 90vw;
  }

  .text {
    width: 30em;
  }
  .pink-line {
    display: block !important;
    width: 4px;
    height: 30em;
    margin: 0 6em 0 16em;
    padding: 0;
    background-color: var(--pink);
  }
}

.pink-line {
  display: none;
}

.image-and-text {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  margin-top: calc(var(--section-gap) / 2);
}

.picture-frame {
  width: 17rem;
  height: 15rem;
  background-image: url("../assets/images/mecoding.webp");
  background-size: cover;
  border-radius: 50px;
  box-shadow: black 0px 0px 5px;
}

.text {
  margin-top: 1rem;
  padding: 30px;
  text-align: justify;
}
</style>
