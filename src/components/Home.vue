<script setup lang="ts">
import HeaderComponent from './Header.vue';
import Layout from './Layout.vue';
import Resume from './Resume/index.vue';
import Movements from './Movements/index.vue';
import { ref } from 'vue';

const amount = ref<number | undefined>(undefined);

amount.value = 1000;

const movementsList = ref([
  {
    id: 0,
    title: 'Compras del mercado',
    description: 'Gastos para la compra de la semana',
    amount: -5000,
  },
  {
    id: 1,
    title: 'Pago deudas',
    description: 'Pago de deudas del mes',
    amount: -800,
  },
  {
    id: 2,
    title: 'Cobro deudas',
    description: 'Cobro de deudas del mes',
    amount: 8000,
  },
  {
    id: 3,
    title: 'Movimiento 4',
    description:
      'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequuntur',
    amount: -400,
  },
  {
    id: 4,
    title: 'Movimiento 5',
    description:
      'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequuntur',
    amount: 5000,
  },
  {
    id: 5,
    title: 'Movimiento 6',
    description:
      'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequuntur',
    amount: 10000,
  },
]);
</script>

<template>
  <Layout>
    <template #header>
      <HeaderComponent />
    </template>
    <template #resume>
      <Resume
        :label="'04/11/2022'"
        :total-label="'Ahorro total'"
        :amount="amount"
        :total-amount="50000"
      >
        <template #graphic>graphic</template>
        <template #action>action</template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movementsList" />
    </template>
  </Layout>
</template>

<style scoped></style>
