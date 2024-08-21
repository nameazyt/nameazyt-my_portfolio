<template>
  <v-container fluid class="contact-container">
    <v-row align="center" justify="center" class="fill-height">
      <v-col cols="12" md="8" lg="6" class="d-flex flex-column align-center">
        <h1 class="display-1 mb-2">Let's work together.</h1>
        <p class="subtitle-1 mb-4">
          Or reach us via : <a href="https://www.gmail.com">nitishkumarsharma.1997@gmail.com</a>
        </p>

        <v-card class="pa-6 contact-card">
          <v-form @submit.prevent="sendEmail" ref="form" v-model="valid" lazy-validation>
            <v-row>
              <v-col cols="12" sm="6">
                <v-text-field
                  v-model="firstName"
                  label="First name"
                  :rules="nameRules"
                  outlined
                  dense
                  prepend-inner-icon="mdi-account"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6">
                <v-text-field
                  v-model="lastName"
                  label="Last name"
                  :rules="nameRules"
                  outlined
                  dense
                  prepend-inner-icon="mdi-account"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-text-field
              v-model="email"
              label="Email"
              :rules="emailRules"
              outlined
              dense
              prepend-inner-icon="mdi-email"
              required
              class="mb-4"
            ></v-text-field>
            <v-textarea
              v-model="message"
              label="Message"
              :rules="messageRules"
              outlined
              dense
              required
              class="mb-4"
            ></v-textarea>
            <v-row justify="end">
              <v-col cols="6">
                <v-btn :disabled="!valid" color="primary" block @click="submit">
                  Send message
                </v-btn>
              </v-col>
            </v-row>
            <v-row justify="center" class="mt-8 social-icons">
              <v-btn icon="mdi-github" href="https://github.com/nameazyt" target="_blank"></v-btn>
              <v-btn
                icon="mdi-instagram"
                href="https://www.instagram.com/_nameazy_/"
                target="_blank"
              ></v-btn>
              <v-btn
                icon="mdi-linkedin"
                href="https://www.linkedin.com/in/nitish-sharma-64b541207/"
                target="_blank"
              ></v-btn>
            </v-row>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
    <v-snackbar :timeout="2000" :color="snackBarColor" v-model="snackBarActivator">
      <strong>{{ snackBarMessage }}</strong>
    </v-snackbar>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'
import emailjs from '@emailjs/browser'
const valid = ref(false)
const form = ref(null)
const firstName = ref('')
const lastName = ref('')
const email = ref('')
const message = ref('')
const snackBarColor = ref('')
const snackBarActivator = ref(false)
const snackBarMessage = ref('')

const nameRules = [
  (v) => !!v || 'Name is required',
  (v) => (v && v.length >= 2) || 'Name must be at least 2 characters'
]
const emailRules = [
  (v) => !!v || 'E-mail is required',
  (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid'
]
const messageRules = [
  (v) => !!v || 'Message is required',
  (v) => (v && v.length >= 10) || 'Message must be at least 10 characters'
]

const submit = () => {
  if (form.value.validate()) {
    sendEmail()
  }
}

const resetForm = () => {
  form.value.reset()
  form.value.resetValidation()
}

const sendEmail = async () => {
  try {
    const serviceID = 'service_uffph4s' // Replace with your EmailJS service ID
    const templateID = 'template_vvdt8g3' // Replace with your EmailJS template ID
    const publicKey = 'uco_TvZvJqR_do-mK' // Replace with your EmailJS user ID
    const form = {
      firstName: firstName.value,
      lastName: lastName.value,
      email: email.value,
      message: message.value
    }

    const response = await emailjs.send(serviceID, templateID, form, publicKey)

    if (response.status === 200) {
      snackBarMessage.value = 'Message sent successfully!'
      snackBarColor.value = 'green'
      snackBarActivator.value = true
      resetForm()
    }
  } catch (error) {
    snackBarColor.value = 'red'
    snackBarMessage.value = 'Failed to send message try again after sometime.'
    snackBarActivator.value = true
    resetForm()
    throw new Error('Failed to send message')
  }
}
</script>

<style scoped>
.contact-container {
  background-color: #000000;
  min-height: 100vh;
  padding: 32px;
}

.display-1 {
  font-weight: bold;
  color: #eeeeee;
  text-align: center;
}

.subtitle-1 {
  color: #7a7a7a;
  text-align: center;
}

.contact-card {
  background-color: rgb(0, 0, 0);
  border-radius: 12px;
  box-shadow: 10 8px 20px rgba(0, 0, 0, 0.1);
  width: 100%;
}

.add-attachment {
  color: #5a5a5a;
}

.add-attachment .v-icon {
  margin-right: 8px;
}

.v-btn--block {
  text-transform: none;
  font-weight: 600;
}

.mb-4 {
  margin-bottom: 16px !important;
}
</style>
