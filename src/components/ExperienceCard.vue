<template>
  <v-card class="ma-12">
    <v-card-title :class="[`bg-${color}`, 'justify-end mb-4']">
      <h2 class="me-4 font-weight-light">{{ title }}</h2>
    </v-card-title>
    <v-card-text>
      {{ Information }}
    </v-card-text>
  </v-card>
</template>

<script setup>
defineProps({
  title: {
    type: String
  },
  Information: {
    type: String
  },
  color: {
    type: String
  }
})
</script>
