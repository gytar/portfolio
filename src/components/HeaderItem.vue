<template>
  <div class="header">
    <h1>
      <slot name="title"></slot>
    </h1>
    <div class="line"></div>
  </div>
</template>
<style scoped>
@import "@/assets/base.css";
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  text-align: center;
  background-color: var(--light-blue-faded);
  padding: 1.5rem 2rem;
  font-size: 2.5em;
}

.line {
  background-color: var(--light-blue);
  width: calc(100% - 4rem);
  height: 4px;
  margin-top: 30px;
}

@media (min-width: 1024px) {
  .line {
    width: calc(100% + 5em);
  }
}

@media (min-width: 1024px) {
  .h1 {
    font-size: 3em;
  }
}
</style>
