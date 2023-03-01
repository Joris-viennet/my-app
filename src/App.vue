<template>
  <header>
    <div class="header">
      <a href="/">Home</a>
      <a href="/about">About</a>
      <a href="/non-existent-path">Broken Link</a>
    </div>
  </header>
  <component :is="currentView" />
</template>

<script>
import Home from './components/Home/Home.vue'
import About from './components/About.vue'
import NotFound from './components/NotFound.vue'

const routes = {
  '/': Home,
  '/about': About
}

export default {
  data() {
    return {
      currentPath: window.location.pathname
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath] || NotFound
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.pathname
    })
  }
}
</script>

<style scoped>
.header {
  margin: 10px;
  padding: 15px;
  border: 2px solid;
  border-color: grey;
  border-radius: 10px;
}
</style>
