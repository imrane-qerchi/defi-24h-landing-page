<script setup lang="ts">
import { ref } from 'vue';

// Date cible : 17 janvier à 18h00
const targetDate = new Date('2025-01-17T18:00:00');

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

const updateCountdown = () => {
  const now = new Date().getTime();
  const distance = targetDate.getTime() - now;

  if (distance > 0) {
    days.value = Math.floor(distance / (1000 * 60 * 60 * 24));
    hours.value = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    minutes.value = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    seconds.value = Math.floor((distance % (1000 * 60)) / 1000);
  } else {
    days.value = 0;
    hours.value = 0;
    minutes.value = 0;
    seconds.value = 0;
  }
};

// Mise à jour initiale et intervalle pour mise à jour continue
updateCountdown();
setInterval(updateCountdown, 1000);
</script>

<template>
  <div class="flex justify-center items-center space-x-4 text-white font-poppins">
    <div class="text-center">
      <p class="text-3xl font-bold">{{ days }}</p>
      <p class="text-sm">Jours</p>
    </div>
    <div class="text-center">
      <p class="text-3xl font-bold">{{ hours }}</p>
      <p class="text-sm">Heures</p>
    </div>
    <div class="text-center">
      <p class="text-3xl font-bold">{{ minutes }}</p>
      <p class="text-sm">Minutes</p>
    </div>
    <div class="text-center">
      <p class="text-3xl font-bold">{{ seconds }}</p>
      <p class="text-sm">Secondes</p>
    </div>
  </div>
</template>