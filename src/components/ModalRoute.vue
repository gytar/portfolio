<script>
export default {
  props: {
    show: Boolean,
    experience: Object,
  },
  data() {
    return {
      url: "",
    };
  },
  mounted() {
    this.url = window.location.protocol + "//" + window.location.host;
  },
};
</script>

<template>
  <Transition name="modal" appear>
    <div v-if="show" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <a href="#" class="close" @click="$emit('close')"></a>
          <div class="modal-header">
            <h3>{{ experience.title }}</h3>
            <h4>{{ experience.subtitle }}</h4>
          </div>

          <div class="modal-content">
            <h4>Description</h4>
            <p>{{ experience.description }}</p>
            <h4>Technologies</h4>
            <div class="logos">
              <img
                v-for="technology in experience.technologies"
                v-bind:key="technology.name"
                :src="url + '/languages-logos/' + technology.name + '.webp'"
                alt="logo programming language"
              />
            </div>
          </div>

          <div class="modal-footer">
            <slot name="footer"> default footer </slot>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style>
.logos {
  margin: 0 auto;
  width: 80%;
}
.logos img {
  width: 50px;
  margin: 1rem;
}

.modal-wrapper p,
.modal-wrapper h3,
.modal-wrapper h4,
.modal-wrapper span,
.modal-wrapper a {
  color: var(--black);
}

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 100%;
  height: 100%;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}
.modal-header {
  width: 90vw !important;
}
.modal-header h3 {
  font-size: 2.5em;
  margin-top: 0;
}

.modal-header h4 {
  margin: 10px 0;
  color: var(--light-blue);
}

.modal-body {
  margin: 20px 0;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: translateY(20px);
}

.modal-enter-active .modal-container,
.modal-leave-active .modal-container {
  transition: all 0.5s ease-in-out;
}

.close {
  position: absolute;
  right: 32px;
  top: 32px;
  width: 32px;
  height: 32px;
  opacity: 0.3;
  z-index: 9999;
}
.close:hover {
  opacity: 1;
}
.close:before,
.close:after {
  position: absolute;
  left: 15px;
  content: " ";
  height: 33px;
  width: 2px;
  background-color: #333;
}
.close:before {
  transform: rotate(45deg);
}
.close:after {
  transform: rotate(-45deg);
}

@media (min-width: 1024px) {
  .modal-container {
    width: 60vw;
    height: 70vh;
  }
  .modal-header h3 {
    font-size: 3em;
  }
}
</style>
