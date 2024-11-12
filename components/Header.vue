<template>
  <nav class="bg-gray-800 py-4 w-full z-50">
    <div class="max-w-7xl mx-auto py-4 px-4 sm:px-6 lg:px-8 flex justify-center items-center">
      <div class="flex items-center space-x-6">
        <a 
          href="#"
          @click.prevent="scrollToSection(1)"
          :class="{ 'text-gray-400': activeTab !== 1, 'text-white textShadow duration-200': activeTab === 1 }"
        >
        Qui suis-je ?
        </a>
        <a
          href="#"
          @click.prevent="scrollToSection(2)"
          :class="{ 'text-gray-400': activeTab !== 2, 'text-white textShadow': activeTab === 2 }"
        >
        Mes projets & expériences
        </a>
        <a
          href="#"
          @click.prevent="scrollToSection(3)"
          :class="{ 'text-gray-400': activeTab !== 3, 'text-white textShadow': activeTab === 3 }"
        >
        Me contacter
        </a>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['scrollToSection'])

const props = defineProps({
  activeTab: {
    type: Number,
    required: true
  }
})

const scrollToSection = (tab) => {
    emit('scrollToSection', tab)
}
</script>

<style lang="scss">

nav {
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
}

.textShadow {
    text-shadow:
        0 0 7px #fff,
        0 0 8px #fff,
        0 0 17px #fff,
}
</style>