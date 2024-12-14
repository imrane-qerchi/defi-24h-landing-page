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
  <div
    class="flex flex-col lg:flex-row justify-center items-center space-y-4 lg:space-y-0 lg:space-x-4 text-transparent font-poppins opacity-50"
    style="-webkit-text-stroke: 6px white"
  >
    <div class="flex items-baseline">
      <p class="text-9xl lg:text-[250px] font-bold">{{ days }}</p>
      <span class="ml-2 text-5xl lg:text-7xl font-medium">j</span>
    </div>
    <div class="flex items-baseline">
      <p class="text-9xl lg:text-[250px] font-bold">{{ hours }}</p>
      <span class="ml-2 text-5xl lg:text-7xl font-medium">h</span>
    </div>
    <div class="flex items-baseline">
      <p class="text-9xl lg:text-[250px] font-bold">{{ minutes }}</p>
      <span class="ml-2 text-5xl lg:text-7xl font-medium">m</span>
    </div>
    <div class="flex items-baseline">
      <p class="text-9xl lg:text-[250px] font-bold">{{ seconds }}</p>
      <span class="ml-2 text-5xl lg:text-7xl font-medium">s</span>
    </div>
  </div>
</template>