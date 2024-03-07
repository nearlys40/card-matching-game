<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="card">{{ value }}</div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  value: {
    type: Number,
    required: true,
  },
});
</script>

<style></style>
