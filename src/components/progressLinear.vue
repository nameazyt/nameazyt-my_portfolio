<template>
  <div class="main">
    <h4>{{ skillsTitle }}</h4>
    <v-progress-linear :model-value="progressLinearValueRef" :color="color" height="25">
      <template v-slot:default="{ value }">
        <strong>{{ Math.ceil(value) }}%</strong>
      </template>
    </v-progress-linear>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const props = defineProps({
  skillsTitle: {
    type: String
  },
  progressLinearValue: {
    type: Number
  },
  color: {
    type: String
  }
})

const progressLinearValueRef = ref(0)

function progressCircularValueUpdate() {
  if (progressLinearValueRef.value === props.progressLinearValue) return true
  progressLinearValueRef.value = progressLinearValueRef.value + 5
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
<style></style>
