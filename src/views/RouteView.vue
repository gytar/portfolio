<script>
import ModalRoute from "@/components/ModalRoute.vue";
import HeaderItem from "@/components/HeaderItem.vue";
import "animate.css";
export default {
  components: {
    ModalRoute,
    HeaderItem,
  },
  data() {
    return {
      showModal: false,
      experience: null,
      experiences: [],
    };
  },
  methods: {
    showDetails(experience) {
      this.experience = experience;
      this.showModal = true;
    },
  },
  mounted() {
    const wellnessPrevention = {
      id: 1,
      title: "Wellness Prévention",
      subtitle: "2021-2022 (Stage 4 mois)",
      description:
        "J'ai contribué à la conception et au développement d'une application web et mobile dans le secteur de la prévention santé. J'ai monté en compétences lors de ce stage sur Symfony et Flutter, en développant des nouvelles fonctionnalités. J'ai aussi pris des décisions technologiques sur Flutter.",
      imageName: "wellness-prevention.webp",
      link: "https://wellness-prevention.fr/",
      technologies: [
        { name: "symfony" },
        { name: "html" },
        { name: "css" },
        { name: "js" },
        { name: "flutter" },
        { name: "git" },
        { name: "docker" },
      ],
      date: "octobre 2021 - février 2022",
    };
    const humanBooster = {
      id: 2,
      title: "Human Booster",
      subtitle: "2021 (Formation)",
      description:
        "Formation niveau BAC+3/4 pour être concepteur développeur d'applications web et mobile sur 1 an. J'ai mis en pratique beaucoup de technologies, et approfondi mes connaissances dans le développement web et mobile. En plus des technologies ci-dessous, j'ai appris à utiliser des outils de conception sur le design et les bases de données tels que Figma, Adobe XD, UML, Merise et aussi de gestions d'entrerprise tels que Scrum.",
      imageName: "human-booster.webp",
      link: "https://humanbooster.com/",
      technologies: [
        { name: "symfony" },
        { name: "java" },
        { name: "mySQL" },
        { name: "css" },
        { name: "js" },
        { name: "android" },
        { name: "electron" },
        { name: "docker" },
        { name: "selenium" },
        { name: "angular" },
        { name: "php" },
        { name: "html" },
        { name: "spring-boot" },
        { name: "gitlab" },
        { name: "sass" },
      ],
      date: "avril 2021 - février 2022",
    };
    const cyberfull = {
      id: 3,
      title: "Cyberfull",
      subtitle: "2020 (POEC)",
      description:
        "Préparation opérationnelle à l’emploi collective (POEC) sur 3 mois dans laquelle j'ai appris les bases de la cybersécurité sur les applications informatique. J'ai réalisé une application desktop en Java dans le cadre d'un fil rouge. J'ai appris beaucoup sur la base de données, la Conception Orientée Objet, docker, git, et autres",
      imageName: "cyberfull.webp",
      link: "https://cyberfull.fr/",
      technologies: [
        { name: "java" },
        { name: "mySQL" },
        { name: "kali" },
        { name: "bash" },
        { name: "docker" },
        { name: "git" },
        { name: "github" },
      ],
      date: "décembre 2020 - mars 2021",
    };
    this.experiences.push(wellnessPrevention);
    this.experiences.push(humanBooster);
    this.experiences.push(cyberfull);
  },
};
</script>

<template>
  <section class="route">
    <HeaderItem>
      <template #title>Parcours</template>
    </HeaderItem>
    <div class="experience-map">
      <TransitionGroup
        name="fadeYIn"
        enter-active-class="animate__animated animate__zoomIn"
        appear
      >
        <div
          class="experience-map-item"
          v-for="experience in experiences"
          v-bind:key="experience.id"
          v-bind:class="experience.id"
          :data-index="experience.id"
          @click="showDetails(experience)"
        >
          <div class="experience-map-item-title">{{ experience.title }}</div>
          <div class="experience-map-item-date">{{ experience.date }}</div>
        </div>
      </TransitionGroup>
    </div>
    <Teleport to="body" v-if="showModal">
      <ModalRoute
        v-bind:experience="experience"
        :show="showModal"
        @close="showModal = false"
      >
      </ModalRoute>
    </Teleport>
  </section>
</template>

<style>
.experience-map {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

.experience-map-item:hover {
  transform: scale(1.05);
  transition: 0.3s ease-in-out;
}

.experience-map-item {
  cursor: pointer;
  background-color: var(--pink);
  width: 20rem;
  height: 10rem;
  padding: 2rem;
  margin: 1rem;
  border-radius: 0.5rem;
}

.experience-map-item-title {
  font-size: 1.5rem;
  font-family: var(--rubik);
  color: var(--white);
}

@media (min-width: 1024px) {
  .route {
    display: flex;
    align-items: center;
    flex-direction: column;
  }
  .experience-map {
    flex-direction: row !important;
    margin-top: 3rem;
  }
}
</style>
