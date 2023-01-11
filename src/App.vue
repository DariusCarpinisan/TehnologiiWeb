<script setup>
import Home from "./pages/Home/Home.vue";
import Stats from "./pages/Stats/Stats.vue";
import About from "./pages/About/About.vue";
</script>

<script>
const routes = {
  "/": Home,
  "/stats": Stats,
  "/about": About,
};

export default {
  data() {
    return {
      currentPath: window.location.pathname,
    };
  },
  computed: {
    currentView() {
      return routes[this.currentPath] || NotFound;
    },
  },
  methods: {
    goToRoute(path) {
      this.currentPath = path;
      window.history.pushState({}, "", path);
    },
  },
  mounted() {
    window.addEventListener("popstate", () => {
      this.currentPath = window.location.pathname;
    });
  },
};
</script>

<template>
  <main>
    <div>
      <div class="nav">
        <button class="home" @click="goToRoute('/')"><span>Home</span></button>
        <button class="stats" @click="goToRoute('/stats')"><span>Stats</span></button>
        <button class="about" @click="goToRoute('/about')"><span>About</span></button>
      </div>
    </div>
    <component :is="currentView" />
  </main>
</template>

<style>
</style>
