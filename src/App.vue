<script setup lang="ts">
// import Home from '@/components/Home.vue';
import SplashScreen from './components/SplashScreen.vue';
import { defineAsyncComponent } from 'vue';

const Home = defineAsyncComponent(async () => {
  await new Promise((resolve) => {
    setTimeout(resolve, 3000);
  });

  // Luego de 3 segundos, cargamos el componente de inicio
  return import('./components/Home.vue');
});
</script>

<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
