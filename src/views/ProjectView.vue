<script>
import HeaderItem from "@/components/HeaderItem.vue";
import ModalProject from "@/components/ModalProject.vue";
export default {
  components: {
    HeaderItem,
    ModalProject,
  },
  data() {
    return {
      showModal: false,
      project: null,
      projects: [],
    };
  },
  methods: {
    showDetails(project) {
      this.project = project;
      this.showModal = true;
    },
  },
  mounted() {
    const leboncoin = {
      id: 1,
      title: "Leboncoin-Like",
      description:
        "Développement d'une application comme leboncoin en PHP Symfony",
      link: "https://github.com/gytar/symfony-exam",
      technologies: [
        { name: "symfony" },
        { name: "html" },
        { name: "css" },
        { name: "js" },
        { name: "git" },
        { name: "bootstrap" },
      ],
    };
    const backUpScript = {
      id: 2,
      title: "Script de sauvegarde linux",
      description:
        "Développement d'un script pour sauvegarder les données de mon PC sur un DD externe",
      link: "https://github.com/gytar/bakuplinux",
      technologies: [
        { name: "bash" },
        { name: "git" },
        { name: "linux" },
        { name: "python" },
      ],
    };
    const youtubeApiAndroid = {
      id: 3,
      title: "Youtube API Android",
      description:
        "Développement d'une application Android pour lire les vidéos de Youtube",
      link: "https://github.com/gytar/youtube-app-android",
      technologies: [
        { name: "java" },
        { name: "android" },
        { name: "google-console" },
        { name: "youtube-api" },
        { name: "git" },
      ],
    };

    this.projects.push(leboncoin);
    this.projects.push(backUpScript);
    this.projects.push(youtubeApiAndroid);
  },
};
</script>

<template>
  <section class="project">
    <HeaderItem>
      <template #title>Projets</template>
    </HeaderItem>

    <div class="project-map">
      <TransitionGroup name="custom-project" enter-active-class="animate__animated animate__fadeInUp animate" appear>
        <div
          class="project-map-item"
          v-for="project in projects"
          :key="project.id"
          :class="project.id"
          @click="showDetails(project)"
        >
          <div class="project-map-title">{{ project.title }}</div>
        </div>
      </TransitionGroup>
    </div>
    <Teleport to="body" v-if="showModal">
      <ModalProject
        v-bind:project="project"
        :show="showModal"
        @close="showModal = false"
      >
      </ModalProject>
    </Teleport>
  </section>
</template>

<style>
.project-map {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

.project-map-item:hover {
  transform: scale(1.05);
  transition: 0.3s ease-in-out;
}

.project-map-item {
  cursor: pointer;
  background-color: var(--pink);
  width: 20rem;
  height: 10rem;
  padding: 2rem;
  margin: 1rem;
  border-radius: 0.5rem;
}

.project-map-title {
  font-size: 1.5rem;
  font-family: var(--rubik);
  color: var(--white);
}

@media (min-width: 1024px) {
  .project {
    display: flex;
    align-items: center;
    flex-direction: column;
  }
  .project-map {
    flex-direction: row !important;
    margin-top: 3rem;
  }
}
</style>
