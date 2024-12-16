<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import { ref } from 'vue'
import CountdownTimer from '@/components/CountdownTimer.vue'
import PocketBase from 'pocketbase'

const pb = new PocketBase('https://defi-24h-mmi.pockethost.io/')
const email = ref('')

const handleSubmit = async () => {
  try {
    await pb.collection('subscribers').create({ email: email.value })
    alert("Merci ! Vous serez informé à l'ouverture des inscriptions.")
    email.value = ''
  } catch (error) {
    console.error("Erreur lors de l'enregistrement :", error)
    alert("Une erreur s'est produite. Veuillez réessayer.")
  }
}
</script>

<template>
  <div
    class="min-h-screen bg-primary-blue text-white font-poppins flex flex-col lg:flex-row items-center relative"
  >
    <!-- Left Side: Text and Countdown -->
    <div class="flex-1 lg:pl-20 flex flex-col items-start">
      <img src="/logo-defi24h.svg" alt="Défi 24H" class="w-40 lg:w-56 lg:mb-8 self-center" />
      <div class="mt-12 mb-10 lg:mb-8 order-1 lg:order-2">
        <h1 class="text-3xl lg:text-5xl font-bold text-primary-yellow">We are</h1>
        <h2 class="text-4xl lg:text-6xl font-bold text-primary-yellow">Coming Soon.</h2>
        <p class="text-xl lg:text-2xl font-bold mt-4">17 Janvier 2025</p>
      </div>
      <CountdownTimer class="order-2 lg:order-1 mb-10 lg:mb-0 w-full max-w-screen-lg mx-auto" />
    </div>

    <!-- Right Side: Form -->
    <div class="lg:absolute bottom-10 right-10 w-full max-w-md mb-16 lg:mb-10 px-4">
      <p class="mb-4 text-base text-center lg:text-left">
        Être notifié à l'ouverture des inscriptions
      </p>
      <form
        class="flex items-center border border-gray-300 rounded-full overflow-hidden"
        @submit.prevent="handleSubmit"
      >
        <input
          type="email"
          v-model="email"
          placeholder="Email"
          class="w-3/4 px-4 py-2 text-black border-none focus:outline-none"
          required
        />
        <button
          type="submit"
          class="w-1/4 bg-black text-white px-4 py-2 rounded-r-xl hover:bg-gray-800 transition flex justify-center items-center whitespace-nowrap"
        >
          S'abonner
        </button>
      </form>
    </div>
  </div>
</template>
