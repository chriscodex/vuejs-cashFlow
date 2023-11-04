<script setup lang="ts">
import HeaderComponent from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/index.vue';
import Movements from './Movements.vue';
import { ref } from 'vue';

const amount = ref<number | undefined>(undefined)

amount.value = 1000
</script>

<template>
  <Layout>
    <template #header>
      <HeaderComponent />
    </template>
    <template #resume>
      <Resume :label="'04/11/2022'" :total-label="'Ahorro total'" :amount="amount" :total-amount="50000">
        <template #graphic>graphic</template>
        <template #action>action</template>
      </Resume>
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

<style scoped></style>
