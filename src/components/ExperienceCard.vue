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

<style>
 .v-card {
  padding: 16px;
  box-shadow: none;
}

.v-card-title {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 8px;
  font-size: 1.5rem;
}

.v-card-text {
  font-size: 1rem;
  padding: 8px;
}

/* Media query for screens less than 600px wide */
@media (max-width: 600px) {
  .v-card {
    margin: 8px;
    padding: 12px;
  }

  .v-card-title {
    font-size: 1.25rem;
    padding: 4px;
    text-align: center;
  }

  .v-card-text {
    font-size: 0.875rem;
    padding: 4px;
  }

  .v-card-title h2 {
    margin-right: 0;
    margin-bottom: 8px;
  }
}

/* Additional media query for screens less than 400px wide */
@media (max-width: 400px) {
  .v-card-title {
    font-size: 1rem;
  }

  .v-card-text {
    font-size: 0.75rem;
  }
}

</style>
