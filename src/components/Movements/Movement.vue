<script setup lang="ts">
import { defineProps, toRefs, computed, defineEmits } from 'vue';

const currencyFormatter = new Intl.NumberFormat('es-PE', {
  style: 'currency',
  currency: 'PEN',
});

const props = defineProps({
  id: {
    type: Number,
  },
  title: {
    type: String,
  },
  description: {
    type: String,
  },
  amount: {
    type: Number,
  },
});

const { id, title, description, amount } = toRefs(props);

const amountCurrency = computed(() => {
  if (typeof amount === 'undefined') {
    return;
  }
  return currencyFormatter.format(amount.value || 0);
});

const isNegative = computed(() => {
  if (typeof amount === 'undefined' || typeof amount.value === 'undefined') {
    return;
  }
  return amount.value < 0;
});

const remove = () => {
  if (typeof id === 'undefined') {
    return;
  }
  emit('remove', id.value);
};

const emit = defineEmits(['remove']);
</script>

<template>
  <div class="movement">
    <div class="content">
      <h4>{{ title }}</h4>
      <p>{{ description }}</p>
    </div>
    <div class="action">
      <img src="@/assets/trash-icon.svg" alt="delete" @click="remove" />
      <p :class="{ red: isNegative, green: !isNegative }">
        {{ amountCurrency }}
      </p>
    </div>
  </div>
</template>

<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}
.movement .content {
  width: 100%;
}
.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}
h4,
p {
  margin: 0;
  padding: 0;
}
h4 {
  margin-bottom: 8px;
}
.movement .action img {
  margin-bottom: 16px;
}
.red {
  color: red;
}
.green {
  color: green;
}
</style>
