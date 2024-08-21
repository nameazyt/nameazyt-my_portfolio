<template>
  <v-container class="main-container">
    <v-row class="mb-6" no-gutters>
      <v-col md="5">
        <v-container class="profile-pic-container">
          <img src="../assets/pic.png" alt="Profile Picture" class="profile-pic" />
        </v-container>
      </v-col>
      <v-col md="7" class="home-text-container">
        <div>
          <div class="home-text-container">
            <div class="home-subtext mb-6">About Me</div>
            <div class="text-first home-text">
              Aspiring Software Engineer | Web Developer | Problem Solver<br />
              I am a B-tech (Computer Science & Engineering) student from Noida Institute of
              Technology. I am a very persistent and hard-working individual, always keen to learn
              new things. I possess a solid understanding of Data Structures and Algorithms and have
              a strong aptitude for problem-solving. I'm a self-taught Web Developer. My other
              fields of interest include astrophysics, practical chemistry, and applied physics.
            </div>
            <v-btn class="mt-6" @click="downloadPDF('myResume.pdf')" traget="_blank" color="primary"
              >Download CV</v-btn
            >
          </div>
        </div>
      </v-col>
    </v-row>
    <v-row no-gutters>
      <v-col>
        <h1 class="experience_heading">My Experience</h1>
      </v-col>
    </v-row>
    <v-row class="heading">
      <v-timeline align="start" justify="center">
        <v-timeline-item
          v-for="(item, index) in experienceData"
          :key="index"
          :dot-color="item.color"
          :size="item.size"
          fill-dot
          width="600"
          dense
        >
          <ExperienceCard
            :title="item.title"
            :Information="item.description"
            :color="item.color"
          ></ExperienceCard>
        </v-timeline-item>
      </v-timeline>
    </v-row>
  </v-container>
</template>

<script setup>
import ExperienceCard from '../components/ExperienceCard.vue'
import { ref } from 'vue'
import axios from 'axios'

const downloadPDF = async (fileName) => {
  try {
    const filePath = `/${fileName}`
    const response = await axios.get(filePath, {
      responseType: 'blob'
    })
    const blob = new Blob([response.data], { type: 'application/pdf' })
    const blobURL = window.URL.createObjectURL(blob)
    const anchor = document.createElement('a')
    anchor.href = blobURL
    anchor.download = fileName
    anchor.click()
    window.URL.revokeObjectURL(blobURL)
  } catch (error) {
    console.error('Error downloading the PDF:', error)
  }
}
const experienceData = ref([
  {
    title: 'Software Engineer I',
    description: `Software Engineer at Helmerich&Payne. Frontend Engineer with 2 years of experience
                specializing in Vue.js, focused on delivering responsive and dynamic web
                applications. Passionate about building clean, efficient code and continuously
                learning new technologies.`,
    color: 'amber-lighten-1',
    size: 'large'
  },
  {
    title: 'Freelance',
    description: `I am a skilled freelance web developer with a strong focus on creating responsive,
                dynamic websites and web applications.
                With experience in modern frontend technologies like Vue.js,
                I am passionate about building clean, efficient code that delivers seamless user experiences.
                Whether you're looking for a complete website overhaul or new custom features,
                I am dedicated to bringing your vision to life through innovative and effective web solutions.`,
    color: 'purple-lighten-2',
    size: 'x-small'
  },
  {
    title: 'Internship',
    description: `I have completed an internship as a web developer,
                 where I gained hands-on experience in building dynamic websites and applications.
                 During this time, I honed my skills in front-end development and 
                 worked with modern technologies to create efficient and responsive web solutions.`,
    color: 'cyan-lighten-1',
    size: 'large'
  },
  {
    title: '12th',
    description: `I completed my 12th in the science stream from Ursuline Convent School.
                  I am a self-taught web developer with additional interests in astrophysics,
                  practical chemistry, and applied physics.`,
    color: 'red-lighten-1',
    size: 'x-small'
  }
])
</script>

<style>
.main-container {
  .heading {
    margin-top: 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 5rem;
  }

  .experience_heading {
    margin-top: 4rem;
    display: flex;
    justify-content: center;
    font-size: 2rem;
  }

  .profile-pic-container {
    position: relative;
    top: 3rem;
    left: auto;
    right: auto;
    display: flex;
    justify-content: center;
  }

  .profile-pic {
    width: 450px;
    height: 450px;
    border-radius: 50%;
    border: 8px solid transparent;
    background-clip: padding-box;
    z-index: 1;
  }

  .profile-pic-container::before {
    content: '';
    position: absolute;
    width: 480px;
    height: 480px;
    border-radius: 50%;
    background: linear-gradient(20deg, #00ffef, #ff00e0);
    filter: blur(10px);
    z-index: 0;
    animation: glow 2s infinite alternate;
  }

  @keyframes glow {
    0% {
      filter: blur(10px);
    }
    100% {
      filter: blur(20px);
    }
  }

  .home-text {
    font-size: 1.2rem;
    width: 800px;
    color: white;
  }

  .home-subtext {
    font-size: 2.5rem;
    color: white;
    position: relative;
    display: inline-block;
  }

  .home-subtext::after {
    content: '';
    position: absolute;
    width: 50px;
    height: 3px;
    background-color: white;
    bottom: -2px;
    left: 0;
  }

  .home-text-container {
    position: relative;
    top: 2rem;
  }

  @media (max-width: 1200px) {
    .profile-pic-container {
      top: 2rem;
      left: auto;
      right: auto;
    }

    .profile-pic {
      width: 200px;
      height: 200px;
    }

    .profile-pic-container::before {
      width: 220px;
      height: 220px;
    }

    .home-text {
      font-size: 0.9rem;
    }

    .home-subtext {
      font-size: 1.2rem;
    }

    .home-text-container {
      width: auto;
      top: 1rem;
    }
  }

  @media (max-width: 768px) {
    .profile-pic-container {
      top: 1rem;
    }

    .profile-pic {
      width: 150px;
      height: 150px;
    }

    .profile-pic-container::before {
      width: 170px;
      height: 170px;
    }

    .home-text {
      font-size: 0.8rem;
    }

    .home-subtext {
      font-size: 1rem;
    }

    .home-text-container {
      width: auto;
      top: 1rem;
    }
  }

  @media (max-width: 480px) {
    .heading,
    .experience_heading {
      font-size: 1.5rem;
    }

    .profile-pic-container {
      top: 0.5rem;
    }

    .profile-pic {
      width: 120px;
      height: 120px;
    }

    .profile-pic-container::before {
      width: 140px;
      height: 140px;
    }

    .home-text {
      font-size: 0.7rem;
    }

    .home-subtext {
      font-size: 0.9rem;
    }

    .home-text-container {
      width: auto;
      top: 0.5rem;
    }
  }
}
</style>
