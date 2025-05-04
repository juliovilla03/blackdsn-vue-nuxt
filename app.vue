<template>
  <NuxtLayout>
    <LoadingPage glitchLogo />
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup>
import LoadingPage from "@/components/layout/loading/LoadingPage.vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { register } from 'swiper/element/bundle';
import { onMounted } from 'vue';
import { useRouter, useRoute } from '#app'; // Importar desde #app o desde nuxt

// Registrar plugins
gsap.registerPlugin(ScrollTrigger);
register();

// Configurar redirección a main-demo en modo claro
const router = useRouter();
const route = useRoute();

onMounted(() => {
  // Solo redirigir si estamos en la página principal
  if (route.path === '/') {
    router.push('/fabrika?mode=light');
  }
});
</script>