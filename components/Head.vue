<template>
  <div class="py-12 text-center">
    <div class="w-full justify-center">
      <h1
        ref="titleRef"
        @mousemove="handleMouseMove"
        @mouseleave="resetShadow"
        class="text-6xl font-bold text-gray-800 drop-shadow-[0_4px_5px_rgba(0,0,0,0.4)] transition-shadow duration-200"
        :style="{ textShadow }"
      >
        {{ title }}
      </h1>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  title: {
    type: String,
    required: true
  }
});

const titleRef = ref(null);
const textShadow = ref('');

const handleMouseMove = (event) => {
  const { offsetX, offsetY, target } = event;
  const width = target.offsetWidth;
  const height = target.offsetHeight;

  const xShadow = (offsetX - width / 2) / 10;
  const yShadow = (offsetY - height / 2) / 10;

  textShadow.value = `${xShadow}px ${yShadow}px 10px rgba(0, 0, 0, 0.4)`;
};

const resetShadow = () => {
  textShadow.value = '';
};
</script>