<template>
  <v-row>
    <v-col class="ma-8" align="center" cols="12">
      <h1>Latest Projects</h1>
    </v-col>
  </v-row>
  <v-container>
    <v-row>
      <v-col v-for="(item, index) in ListOfProjects" :key="index" cols="12" md="6">
        <ProjectCard
          :title="item.title"
          :projectSubTitle="item.subTitle"
          :projectContent="item.content"
          :projectImage="item.image"
        ></ProjectCard>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'
import ProjectCard from '../components/ProjectCard.vue'
import WeatherApp from '../assets/WeatherApp.jpg'
import ProductApp from '../assets/ProductApp.PNG'
import ChatApp from '../assets/ChatApp.jpg'
import game from '../assets/game.jpg'

const ListOfProjects = ref([
  {
    title: 'Weather App',
    subTitle: 'Responsive Weather App Project',
    image: WeatherApp,
    content:
      'Weather App: Developed a responsive web application using HTML, CSS, and JavaScript that fetches real-time weather data from an external API. The app allows users to search for current weather conditions by city and dynamically displays temperature, humidity, and weather descriptions. Demonstrated proficiency in API integration and front-end development.'
  },
  {
    title: 'Chat App',
    subTitle: 'Group Chat Application',
    image: ChatApp,
    content:
      'Chat App: Built a real-time chat application using HTML, CSS, JavaScript, and WebSocket integration. The app supports live messaging between users in a responsive interface, demonstrating skills in client-server communication, asynchronous updates, and real-time data handling'
  },
  {
    title: 'Stone Paper Scissor Game',
    subTitle: 'Stone Paper Scissor Game Player Vs CPU',
    image: game,
    content:
      'Stone Paper Scissor Game: Created an interactive Stone Paper Scissor game using HTML, CSS, and JavaScript. The game features a responsive design and logic for user vs. computer gameplay, highlighting skills in DOM manipulation, event handling, and game logic implementation.'
  },
  {
    title: 'E-commerce App',
    subTitle: 'Product Inventory App',
    image: ProductApp,
    content:
      'Ecommerce Project: Developed a fully functional ecommerce website using HTML, CSS, and JavaScript. Implemented features such as product listings, a shopping cart, and checkout functionality, showcasing skills in front-end development, UI/UX design, and basic ecommerce workflows.'
  }
])
</script>
