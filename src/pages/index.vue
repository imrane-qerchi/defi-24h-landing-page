<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import { ref } from 'vue'
import CountdownTimer from '@/components/CountdownTimer.vue'

const email = ref('')

const handleSubmit = () => {
  // Placeholder for handling the email submission
  alert(`Merci ! Votre email (${email.value}) a été enregistré.`)
  email.value = ''
}
</script>

<template>
  <div class="min-h-screen bg-primary-blue flex flex-col lg:flex-row">
    <!-- Left Side: Logo -->
    <div class="lg:w-1/2 w-full flex justify-center items-center p-4">
      <img src="/logo-defi24h.svg" alt="Défi 24H" class="w-3/4 lg:w-1/2" />
    </div>

    <!-- Right Side: Content -->
    <div
      class="lg:w-1/2 w-full flex flex-col justify-center items-center text-center text-white p-4"
    >
      <h1 class="text-5xl lg:text-7xl font-bold mb-4">Coming Soon!</h1>
      <h2 class="text-3xl lg:text-6xl font-bold mb-8">17-18 Janvier</h2>

      <CountdownTimer />

      <form
        class="mt-8 flex flex-col lg:flex-row items-center lg:space-x-4 space-y-4 lg:space-y-0"
        @submit.prevent="handleSubmit"
      >
        <input
          type="email"
          v-model="email"
          placeholder="Entrez votre email"
          class="border border-gray-300 rounded-md px-4 py-2 text-black w-72"
          required
        />
        <button
          type="submit"
          class="bg-primary-yellow text-black font-normal rounded-md px-4 py-2 hover:bg-yellow-500 transition"
        >
          Informez-moi
        </button>
      </form>
    </div>
  </div>
</template>
