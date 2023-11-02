<script setup lang="ts">
import HeaderComponent from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/index.vue';
import Movements from './Movements.vue'
</script>

<template>
  <Layout>
    <template #header>
      <HeaderComponent />
    </template>
    <template #resume>
      <Resume />
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

<style scoped></style>
