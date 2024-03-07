<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="card" @click="selectCard">
    <div v-if="visible" class="card-face is-front">
      <img :src="`/images/${value}.png`" :alt="value" />
      <img v-if="matched" src="/images/checkmark.svg" class="icon-checkmark" />
    </div>
    <div v-else class="card-face is-back"></div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
const props = defineProps({
  matched: {
    type: Boolean,
    default: false,
  },
  position: {
    type: Number,
    required: true,
  },
  value: {
    type: String,
    required: true,
  },
  visible: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(["select-card"]);

const selectCard = () => {
  emit("select-card", {
    position: props.position,
    faceValue: props.value,
  });
};
</script>

<style>
.card {
  position: relative;
}

.card-face {
  width: 100%;
  height: 100%;
  position: absolute;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card-face.is-front {
  background-image: url("/public/images/card-bg.png");
  color: white;
}

.card-face.is-back {
  background-image: url("/public/images/card-bg-empty.png");
  color: white;
}

.icon-checkmark {
  position: absolute;
  right: 5px;
  bottom: 5px;
}
</style>
