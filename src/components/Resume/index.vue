<script setup lang="ts">
import { defineProps, computed } from 'vue';

const props = defineProps({
  totalLabel: {
    type: String,
    default: null,
  },
  label: String,
  amount: Number,
  totalAmount: {
    type: Number,
    default: null,
  },
});

const { totalLabel, label, amount, totalAmount } = props;

const amountVisual = computed(() => {
  if (totalAmount) {
    return totalAmount;
  } else {
    return amount;
  }
});

const labelVisual = computed(() => {
  if (totalLabel) {
    return totalLabel;
  } else {
    return label;
  }
});

const currencyFormatter = new Intl.NumberFormat('es-PE', {
  style: 'currency',
  currency: 'PEN',
});

const amountCurrency = computed(() => {
  if (
    typeof amountVisual.value === 'number' ||
    typeof amountVisual.value === 'bigint'
  )
    return currencyFormatter.format(amountVisual.value);
});
</script>

<template>
  <main>
    <p>
      {{ labelVisual }}
    </p>
    <h1>
      {{ amountCurrency }}
    </h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}
h1,
p {
  margin: 0;
  text-align: center;
}
h1 {
  margin-top: 14px;
  color: var(--brand-green);
}
.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>
