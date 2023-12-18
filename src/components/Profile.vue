<template>
   <div>
    <v-card class="profile-card">
    <v-row class="profile-content">
      <!-- Info Section -->
      <v-col cols="4">
        <!-- Image -->
        <v-img
          class="profile-image"
          :src="profile.image"
          width="250"
          height="250"
          rounded
        ></v-img>
        <!-- Resume -->
        <div class="summary-wrapper">
          <p class="summary-text">{{ profile.summary }} </p>
        </div>
      </v-col>
      <v-col cols="8">
        <!-- Profissional Info Section -->
        <v-card-text class="profile-info">
          <div>
            <h2>{{ profile.name }}</h2>
            <div class="subtitle-1">
              {{ profile.specialty }}
              <span class="separator">|</span>
              {{ profile.address }}
            </div>
            <div class="body-1">
            {{ profile.price }} 
            <span class="separator">|</span>
            {{ profile.time }}
            </div>           
            <v-row >
              <!-- Reviews -->
              <v-rating
                :value="profile.rating"
                color="yellow"
                size="20"
                dense
                half-increments
              ></v-rating>
              <div  class="grey--text">{{ profile.rating }}</div>
            </v-row>
            <div class="subtitle-1"> {{ profile.idiom }}</div>
          </div> 
        </v-card-text>
        <!-- Calendar Section -->
        <calendar></calendar>
      </v-col>
    </v-row>
  </v-card>
  </div>
  </template>

<script>

//

import Calendar from './Calendar.vue';
export default {
  name: 'UserProfile',

  components: {
    calendar: Calendar // Register the Calendar component
  },

    data: () => ({
        profile: {
            image: "https://images.unsplash.com/photo-1651008376811-b90baee60c1f?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
            name: "Dra Anna Castro",
            rating: 4.5,
            specialty: "Psicologia",
            address: "São Paulo",
            summary:'Formada pela Universidade de São Paulo (USP) em 2020. Com vasta experiência no campo da saúde mental, busco oferecer um cuidado compassivo e individualizado aos meus pacientes. Focando no tratamento de transtornos mentais, ansiedade, depressão e estresse pós-traumático. Busco sempre estar atualizada com as mais recentes pesquisas e terapias, meu objetivo e ajudar voce a alcançarem uma saúde mental plena e equilibrada.',
            price: "R$ 100",
            time:"30 minutos",
            idiom:"Português",
        },       
    })
}
</script>

<style scoped src="./ProfileStyle.css"></style>