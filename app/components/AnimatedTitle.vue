<script setup lang="ts">
import { onMounted } from "vue";

const { $gsap } = useNuxtApp();

const text = "Smooth animations with Nuxt & GSAP";

// Transform the text into an array of letters
const letters = text.split("");

onMounted(() => {
  // Animation for each letter with a stagger effect
  $gsap.from(".letter", {
    opacity: 0,
    y: 50,
    stagger: 0.05,
    duration: 0.6,
    ease: "power3.out",
  });

  // Underline animation
  $gsap.from(".underline", {
    scaleX: 0,
    transformOrigin: "left center",
    duration: 0.8,
    delay: letters.length * 0.05, // start after the text
    ease: "power2.out",
  });
});

useHead({
  title: "Animated Title with Nuxt & GSAP",
  meta: [
    {
      name: "description",
      content: "A simple animated title using Nuxt 4 and GSAP.",
    },
  ],
});
</script>

<template>
  <div class="min-h-screen flex flex-col items-center justify-center px-8">
    <h1 class="text-md lg:text-4xl font-bold flex flex-wrap gap-0.5">
      <span
        v-for="(char, index) in letters"
        :key="index"
        class="letter inline-block"
      >
        {{ char === " " ? "\u00A0" : char }}
      </span>
    </h1>
    <div class="underline h-0.5 lg:h-1 bg-green-500 mt-4 w-1/2 rounded"></div>
  </div>
</template>
