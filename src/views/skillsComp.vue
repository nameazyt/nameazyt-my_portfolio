<template>
  <v-container class="main-container">
    <v-row no-gutters>
      <v-col class="heading" cols="12">
        <h1>My</h1>
        <h1 class="skills">Skills</h1>
      </v-col>
    </v-row>

    <v-row class="mt-8" no-gutters>
      <!-- Linear Progress Bars -->
      <v-col class="mt-2" cols="12" md="6">
        <v-row>
          <v-col class="heading" cols="12">
            <h1 class="title" :class="{ 'underline-animation': animateUnderline }">
              Technical<span class="skills">Skills</span>
            </h1>
          </v-col>
          <v-col
            cols="12"
            v-for="(item, index) in ListOfProgressLinearSkills"
            :key="index"
            class="mb-3"
          >
            <progressLinear
              :progressLinearValue="item.value"
              :skillsTitle="item.title"
              :color="item.color"
            ></progressLinear>
          </v-col>
        </v-row>
      </v-col>

      <!-- Circular Progress Bars -->
      <v-col cols="12" md="6">
        <v-row>
          <v-col class="heading" cols="12">
            <h1 class="title" :class="{ 'underline-animation': animateUnderline }">
              Professional<span class="skills">Skills</span>
            </h1>
          </v-col>
          <v-row>
            <v-col
              class="mb-12 text-center"
              v-for="(skill, index) in ListOfProgressCircularSkills"
              :key="index"
              cols="12"
              sm="6"
              lg="6"
            >
              <progressCircular
                :skillsTitle="skill.title"
                :value="skill.value"
                :color="skill.color"
              ></progressCircular>
            </v-col>
          </v-row>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import progressCircular from '../components/progressCircular.vue'
import progressLinear from '../components/progressLinear.vue'
import { ref, onMounted } from 'vue'

const animateUnderline = ref(false)

onMounted(() => {
  // Trigger the animation when the component is mounted
  setTimeout(() => {
    animateUnderline.value = true
  }, 100) // Delay to ensure animation triggers after mounting
})

const ListOfProgressCircularSkills = ref([
  {
    title: 'Creativity',
    value: 90,
    color: 'teal'
  },
  {
    title: 'Communication',
    value: 60,
    color: 'primary'
  },
  {
    title: 'Problem Solving',
    value: 85,
    color: 'amber'
  },
  {
    title: 'Team Work',
    value: 90,
    color: 'red'
  }
])

const ListOfProgressLinearSkills = ref([
  {
    title: 'HTML',
    value: 90,
    color: 'primary'
  },
  {
    title: 'CSS',
    value: 60,
    color: 'teal'
  },
  {
    title: 'JavaScript',
    value: 75,
    color: 'red'
  },
  {
    title: 'Vue.js',
    value: 85,
    color: 'orange'
  },
  {
    title: 'TypeScript',
    value: 65,
    color: 'pink'
  },
  {
    title: 'Git',
    value: 60,
    color: 'grey'
  },
  {
    title: 'C++',
    value: 70,
    color: 'deep-purple-accent-4'
  },
  {
    title: 'OOPs',
    value: 75,
    color: 'black'
  }
])
</script>

<style>
.main-container {
  .heading {
    margin-top: 2rem;
    font-size: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .skills {
    margin-left: 10px;
    color: aqua;
  }

  .text-center {
    margin-top: 3rem;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title {
    position: relative;
    display: inline-block;
    font-size: 32px;
    margin-top: 2rem;
    color: #fff;
  }

  .skills {
    margin-left: 10px;
    color: aqua;
  }

  .title::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 3px;
    background-color: aqua;
    transition: width 0.5s ease-out;
  }

  .underline-animation::after {
    width: 100%;
  }

  @media only screen and (max-width: 600px) {
    .heading {
      font-size: 24px;
      margin-top: 1rem;
    }

    .skills {
      margin-left: 5px;
      font-size: 24px;
    }

    .text-center {
      margin-top: 1.5rem;
    }

    .title {
      font-size: 24px;
      margin-top: 1rem;
    }
  }
}
</style>
