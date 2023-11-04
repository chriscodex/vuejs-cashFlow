<script setup lang="ts">
import { defineProps, toRefs } from 'vue';

const props = defineProps({
  title: {
    type: String,
  },
});

const { title } = toRefs(props);
</script>

<template>
  <div class="movement">{{ title }}</div>
</template>

<style scoped></style>
