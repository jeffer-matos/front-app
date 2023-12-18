<template>
    <div class="calendar">
      <!-- Calendar Header: Days of the Week -->
      <div class="calendar-header">
        
        </div>
      </div>
  
      <!-- Calendar Body: Time Slots for Each Day -->
      <div class="calendar-body">
        
    </div>
  </template>
  
<script>

import axios from 'axios';
  
  export default {
    name: 'Calendar',
    data() {
      return {
        daysOfWeek: ['Dom', 'Seg', 'Ter', 'Qua', 'Qui', 'Sex', 'Sab'],
        days: []
      };
    },
    mounted() {
      this.fetchAvailableSlots();
    },
    methods: {
      fetchAvailableSlots() {
      axios.get('http://localhost:3000/slots')
        .then(response => {
          this.days = response.data;
        })
        .catch(error => {
          // eslint-disable-next-line no-console
          console.error("There was an error fetching the slots:", error);
        });
      }
    },
   };
</script>

<style>
/* Estilo do calendario */
.calendar {
  margin-top: -4rem;
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 8px; 
}

/* Calendar Header: Days of the Week */
.calendar > .grid:first-child {
  background-color: #f3f4f6; 
  border-bottom: 2px solid #e5e7eb; 
}

/* Calendar Day and Slot Styling */
.calendar .grid > div {
  background-color: #fff; 
  border: 1px solid #e5e7eb; 
  border-radius: 8px; 
  padding: 8px; 
  text-align: center;
  cursor: pointer; 
}

/* Hover Effect for Slots */
.calendar .grid > div:hover {
  background-color: #cbd5e1; 
  color: #1f2937; 
}

/* Responsive adjustments (optional) */
@media (max-width: 600px) {
  .calendar {
    grid-template-columns: repeat(3, 1fr); 
  }
}
</style>