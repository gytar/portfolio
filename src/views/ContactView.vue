<script>
import HeaderItem from "@/components/HeaderItem.vue";
import axios from "axios";
export default {
  components: {
    HeaderItem,
  },
  methods: {
    downloadFile() {
      axios({
        url: "/cv-guillaume-perrot.pdf",
        method: "GET",
        responseType: "blob",
      }).then((res) => {
        let file = window.URL.createObjectURL(new Blob([res.data]));
        let docURL = document.createElement("a");
        docURL.href = file;
        docURL.setAttribute("download", "guillaume-perrot.pdf");
        document.body.appendChild(docURL);
        docURL.click();
      });
    },
  },
};
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

    <div class="download-resume" @click="downloadFile()">
      <span>Mon CV</span>
      <i class="bi bi-download"></i>
    </div>
  </section>
</template>

<style>

.contact {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: space-evenly;
  background-color: var(--white);
  min-height: 80vh;
  box-shadow: rgb(29, 29, 29) 0px 0px 10px;
  border-radius: 10px;
}
.contact h1 {
  color: var(--black) !important;
  font-size: 1.5em;
  background-color: var(--pink-faded) !important;
}
.contact h1 + .line {
  background-color: var(--pink) !important;
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
  width: 13rem;
  border: var(--pink) solid 3px;
  border-radius: 10px;
  padding: 0.7em 0.5em;
  color: var(--pink);
  font-size: 1.5em;
  font-family: var(--rubik);
  cursor: pointer;
}

@media (min-width: 374px) {
  .download-resume {
    width: 17rem;
  }
  h1 {
    font-size: 2.5em !important;
  }
}
</style>
