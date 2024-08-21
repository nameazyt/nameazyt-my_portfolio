<template>
  <v-card class="mx-auto hover-card" max-width="344">
    <v-img height="200px" :src="projectImage" cover class="hover-image"></v-img>

    <v-card-title class="hover-title"> {{ projectTitle }}</v-card-title>

    <v-card-subtitle class="hover-subtitle"> {{ projectSubTitle }}</v-card-subtitle>

    <v-card-actions>
      <v-spacer></v-spacer>

      <v-btn
        :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        @click="show = !show"
        class="hover-btn"
      ></v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text class="hover-content">
          {{ projectContent }}
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script setup>
import { ref } from 'vue'

const show = ref(false)
defineProps({
  projectTitle: {
    type: String
  },
  projectSubTitle: {
    type: Number
  },
  projectContent: {
    type: String
  },
  projectImage: {
    type: String
  }
})
</script>

<style scoped>
.hover-card {
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease,
    background-color 0.3s ease;
  background-color: #181818;
  border-radius: 15px;
  overflow: hidden;
}

.hover-card:hover {
  transform: translateY(-8px) rotate(-2deg);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
  background-color: #3187e2;
}

.hover-card:hover::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle at 50% 50%, rgba(255, 255, 255, 0.3), rgba(255, 255, 255, 0));
  transition: opacity 0.5s;
  opacity: 0.6;
  pointer-events: none;
  z-index: -1;
}

.hover-image {
  transition:
    filter 0.3s ease,
    transform 0.3s ease;
}

.hover-card:hover .hover-image {
  filter: brightness(0.8);
  transform: scale(1.05);
}

.hover-title {
  transition: color 0.3s ease;
}

.hover-card:hover .hover-title {
  color: #007bff;
}

.hover-subtitle {
  transition: color 0.3s ease;
}

.hover-card:hover .hover-subtitle {
  color: #555;
}

.hover-content {
  transition:
    transform 0.3s ease,
    opacity 0.3s ease;
}

.hover-card:hover .hover-content {
  transform: translateY(10px);
  opacity: 0.9;
}

.hover-btn {
  position: relative;
  overflow: hidden;
}

.hover-btn::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 300%;
  height: 300%;
  background: rgba(0, 123, 255, 0.4);
  transform: translate(-50%, -50%) scale(0);
  border-radius: 50%;
  transition: transform 0.4s ease;
}

.hover-btn:active::before {
  transform: translate(-50%, -50%) scale(1);
  transition: transform 0.2s ease;
}
</style>
