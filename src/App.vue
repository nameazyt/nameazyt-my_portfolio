<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref, onMounted, watch } from 'vue'

const drawer = ref(false)

// Watch for window resizing and adjust the drawer state accordingly
const handleResize = () => {
  if (window.innerWidth > 968) {
    drawer.value = false
  }
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})

watch(drawer, (newValue) => {
  if (window.innerWidth > 968 && newValue) {
    drawer.value = false
  }
})
</script>

<template>
  <v-app>
    <v-app-bar :elevation="10" mobile>
      <template v-slot:prepend>
        <v-app-bar-nav-icon class="navBar" @click="drawer = !drawer"></v-app-bar-nav-icon>
      </template>
      <v-app-bar-title>Nitish Shamra</v-app-bar-title>
      <nav class="test">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/myInfo">My Info</RouterLink>
        <RouterLink to="/skills">Skills</RouterLink>
        <RouterLink to="/projects">Project</RouterLink>
        <RouterLink to="/contactMe">Contact Me</RouterLink>
      </nav>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item-group>
          <v-list-item to="/" exact>
            <v-list-item-content>
              <v-list-item-title>Home</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/myInfo">
            <v-list-item-content>
              <v-list-item-title>My Info</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/skills">
            <v-list-item-content>
              <v-list-item-title>Skills</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/projects">
            <v-list-item-content>
              <v-list-item-title>Projects</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/contactMe">
            <v-list-item-content>
              <v-list-item-title>Contact Me</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<style scoped>
.v-main {
  background-color: #0c1a2c;
}
.v-list-item {
  display: block;
}
@media (min-width: 968px) {
  .navBar {
    display: none;
  }
}

@media (max-width: 968px) {
  .test {
    display: none;
  }
}

nav {
  text-align: left;
  font-size: 1rem;
  padding: 1rem 0;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0.5rem 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}
</style>
