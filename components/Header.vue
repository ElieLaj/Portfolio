<template> 
  <nav class="bg-white py-4 z-50 shadow-md w-fit mx-auto rounded-2xl mt-4">
    <div class="max-w-7xl mx-auto py-4 px-4 sm:px-6 lg:px-8 flex justify-center items-center">
      <div class="flex items-center space-x-6 flex-wrap justify-center">
        <a 
          href="#"
          @click.prevent="scrollToSection(1)"
          class="title-nav"
          :class="{ 'text-black': activeTab !== 1, 'text-black textShadow': activeTab === 1 }"
        >
          Qui suis-je ?
        </a>
        <a
          href="#"
          @click.prevent="scrollToSection(2)"
          class="title-nav"
          :class="{ 'text-black': activeTab !== 2, 'text-black textShadow': activeTab === 2 }"
        >
          Mes projets & expériences
        </a>
        <a
          href="#"
          @click.prevent="scrollToSection(3)"
          class="title-nav"
          :class="{ 'text-black': activeTab !== 3, 'text-black textShadow': activeTab === 3 }"
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
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.textShadow {
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.3), 
               0 1px 2px rgba(0, 0, 0, 0.2);
}

.title-nav {
  @apply text-center text-xl max-lg:text-base transition duration-200 transform hover:scale-110 font-bold;
}

.title-nav:hover {
  text-shadow: 0 0 12px #fff, 0 0 13px #fff, 0 0 20px #fff;
}
</style>
