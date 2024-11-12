<template>
  <div class="pt-8 pb-16 text-center">
    <div class="w-full justify-center">
      <h1 class="text-6xl font-bold text-gray-800 drop-shadow-[0_4px_5px_rgba(0,0,0,0.4)]">
        {{ title }}
      </h1>
    </div>
  </div>
</template>


<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true
  }
})
</script>