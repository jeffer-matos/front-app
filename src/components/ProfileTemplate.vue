<template>
  <div
    class="max-w-2xl mx-auto p-6 bg-white shadow-lg rounded-lg flex justify-between"
  >
    <!-- Professional Info Section -->
    <div class="flex flex-col justify-start">
      <div class="flex items-center space-x-4">
        <div class="rounded-full h-12 w-12 bg-gray-300">
          <img
            src="https://images.unsplash.com/photo-1651008376811-b90baee60c1f?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
            alt="Profile Picture"
            class="rounded-full w-12 h-12 object-cover"
          />
        </div>
        <div>
          <h2 class="text-xl font-semibold text-black">Anna Castro</h2>
          <p class="text-gray-500">PSICOLOGA | São Paulo</p>
        </div>
      </div>
      <div class="mt-3">
        <p class="text-gray-700 text-sm">
          Formada pela Universidade de São Paulo (USP) em 2020. Com vasta
          experiência no campo da saúde mental, busco oferecer um cuidado
          compassivo e individualizado aos meus pacientes. Focando no tratamento
          de transtornos mentais, ansiedade, depressão e estresse
          pós-traumático. Busco sempre estar atualizada com as mais recentes
          pesquisas e terapias, meu objetivo e ajudar voce a alcançarem uma
          saúde mental plena e equilibrada.
        </p>
      </div>
      <div class="mt-4">
        <span class="text-gray-500 text-sm">(20 reviews)</span>
        <span class="block text-lg font-semibold">R$100 / 50 minutos</span>
      </div>
    </div>

    <!-- Schedule Section -->
    <div class="mt-6">
      <div class="flex justify-between">
        <!-- Days of the week -->
        <div
          v-for="day in days"
          :key="day.date"
          class="flex flex-col items-center"
        >
          <div class="font-bold">{{ day.date }}</div>
          <div class="flex flex-col">
            <!-- Time slots for each day -->
            <div
              v-for="time in day.slots"
              :key="time"
              class="my-2 p-2 border rounded-lg text-center cursor-pointer hover:bg-blue-500 hover:text-white"
            >
              {{ time }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      days: [], // Will be populated with data from the server
    };
  },
  mounted() {
    this.fetchAvailableSlots();
  },
  methods: {
    fetchAvailableSlots() {
    axios.get("http://localhost:3000/slots")
    .then((response) => {
      // Transforma o objeto de datas em um array de objetos com 'date' e 'slots'
      const formattedData = Object.keys(response.data).map((date) => {
        return {
          date: date,
          slots: response.data[date]
        };
      });
      this.days = formattedData;
    })
    .catch((error) => {
      // eslint-disable-next-line no-console
      console.error("There was an error fetching the slots:", error);
    });
    },
  },
};
</script>
