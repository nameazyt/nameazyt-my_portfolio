<script setup></script>

<template>
  <v-container class="home-container">
    <v-row class="align-center animate-sparkle">
      <v-col cols="12" md="6" class="">
        <p class="intro animate-fadeIn">Namaste(); I'm</p>
        <h1 class="name animate-fadeIn">
          <span class="gradient-text">Nitish Sharma</span>
        </h1>
        <h2 class="headline animate-slideIn">I code & build infra for apps</h2>
        <p class="description animate-fadeIn">
          I'm a Vue.js engineer specializing in building dynamic, responsive web applications with a
          focus on performance and seamless user experiences.
        </p>
        <p class="description animate-fadeIn">
          I excel in creating scalable solutions using modern tools and efficient state management.
        </p>
        <v-btn class="talk-btn animate-pulse" color="purple" to="/contactMe" dark>Let's Talk</v-btn>
        <div class="icons">
          <v-icon class="icon animate-bounce">mdi-cog</v-icon>
          <v-icon class="icon animate-bounce">mdi-flask</v-icon>
        </div>
      </v-col>
      <v-col cols="12" md="6" class="image-col">
        <div>
          <img src="../assets/pic.png" alt="Profile Picture" class="profile-pic animate-slideIn" />
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideIn {
  from {
    transform: translateY(20px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes bounce {
  0%,
  20%,
  50%,
  80%,
  100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-10px);
  }
  60% {
    transform: translateY(-5px);
  }
}

.animate-fadeIn {
  animation: fadeIn 2s ease-in;
}

.animate-slideIn {
  animation: slideIn 1.5s ease-out;
}

.animate-pulse {
  animation: pulse 2s infinite;
}

.animate-bounce {
  animation: bounce 2s infinite;
}

.animate-sparkle {
  /* margin: 100px; */
  /* padding: 15px 15px; */
  border: none;
  outline: none;
  color: #fff;
  cursor: pointer;
  position: relative;
  z-index: 1;
  border-radius: 12px;
}
.animate-sparkle::after {
  content: '';
  z-index: -1;
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: #0c1a2c;
  left: 0;
  top: 0;
  border-radius: 10px;
}
/* glow */
.animate-sparkle::before {
  content: '';
  background: linear-gradient(
    45deg,
    #ff0000,
    #ff7300,
    #fffb00,
    #48ff00,
    #00ffd5,
    #002bff,
    #ff00c8,
    #ff0000
  );
  position: absolute;
  top: -2px;
  left: -2px;
  background-size: 600%;
  z-index: -1;
  width: calc(100% + 4px);
  height: calc(100% + 4px);
  filter: blur(8px);
  animation: glowing 20s linear infinite;
  transition: opacity 0.3s ease-in-out;
  border-radius: 10px;
  opacity: 0;
}

@keyframes glowing {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}

/* hover */
.animate-sparkle:hover::before {
  opacity: 1;
}


.home-container {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 90vh;
  max-width: 120vh;
  color: white;
  padding: 50px;
}

.intro {
  font-size: 24px;
  font-weight: 700;
}

.name {
  font-size: 48px;
  font-weight: 900;
}

.gradient-text {
  background: linear-gradient(to right, orange, green);
  -webkit-background-clip: text;
  color: transparent;
}

.headline {
  font-size: 40px;
  font-weight: bold;
  margin-bottom: 24px;
}

.description {
  font-size: 18px;
  margin-bottom: 16px;
}

.talk-btn {
  margin-top: 24px;
  margin-bottom: 24px;
}

.icons {
  margin-top: 24px;
}

.icon {
  font-size: 32px;
  margin: 0 12px;
}

.image-col {
  display: flex;
  justify-content: center;
  align-items: center;
}

.profile-pic {
  width: 100%;
  max-width: 500px;
  border-radius: 20%;
  border: 10px solid transparent;
  background-clip: padding-box;
  z-index: 1;
}
</style>
