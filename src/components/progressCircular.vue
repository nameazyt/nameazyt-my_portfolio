<template>
  <div>
    <v-progress-circular
      :model-value="progressCircularValue"
      :rotate="360"
      :size="150"
      :width="15"
      :color="color"
      class="mb-8"
    >
      {{ progressCircularValue }}
    </v-progress-circular>
    <h2 class="skillsTitle">{{ skillsTitle }}</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const props = defineProps({
  skillsTitle: {
    type: String
  },
  value: {
    type: String
  },
  color: {
    type: String
  }
})

const progressCircularValue = ref(0)

function progressCircularValueUpdate() {
  if (progressCircularValue.value === props.value) return true
  progressCircularValue.value = progressCircularValue.value + 5
}
let intervalId = setInterval(() => {
  if (progressCircularValueUpdate()) {
    clearInterval(intervalId)
    console.log('Condition fulfilled!')
  } else {
    console.log('Trying again...')
  }
}, 50)
</script>
