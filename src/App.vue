<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <div>
    <nav>
      <div class="name">
        {{ username }}
      </div>
      <div>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </div>
    </nav>
    <div class="view">
      <RouterView />
    </div>
  </div>
</template>

<script>
import { mapState } from "pinia";
import { useAuthStore } from "./stores/auth";
  export default {
    computed: {
    ...mapState(useAuthStore, ["username"]),
  },
  }
</script>

<style scoped>

.view {
  display: flex;
  width: 100%;
}
.name {
  padding-left: 1rem;
}

nav {
  background-color: #333;
  color: #fff;
  display: flex;
  justify-content: space-between;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 999;
}

nav a {
  color: #fff;
  text-decoration: none;
}

nav a:hover {
  color: #ddd;
}

header {
  line-height: 1.5;
  max-height: 100vh;
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
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  nav {
    text-align: left;
    font-size: 1rem;

    padding: 1rem 0;
  }
}
</style>
