<template>
    <Header :active-tab="activeTab" @scrollToSection="(tab) => activeTab = tab"/>
    <Home v-if="activeTab == 1" class="transition-transform duration-500 ease-in-out" :direction="direction" />
    <Skills v-if="activeTab == 2" class="transition-transform duration-500 ease-in-out pb-10" :direction="direction" />
    <Contact v-if="activeTab == 3" class="transition-transform duration-500 ease-in-out pb-10" :direction="direction" />
    <div class="flex fixed bottom-0 w-full justify-center my-6 max-lg:my-3 gap-2">
        <button @click="activeTab--" v-if="activeTab > 1" class="arrowButton"><Icon name="uil:arrow-circle-left" style="color: white" class="text-3xl max-lg:text-2xl" /></button>
        <button @click="activeTab++" v-if="activeTab < 3" class="arrowButton"><Icon name="uil:arrow-circle-right" style="color: white" class="text-3xl max-lg:text-2xl" /></button>
    </div>
  <div class="bg-gray-100 fixed w-full h-full top-0 blur bg-[url('/static/images/la_vague.jpg')] bg-cover -z-10">
  </div>

</template>

<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue'
import Header from '../components/Header.vue';
import Home from '../components/Home.vue';
import Skills from '../components/Skills.vue';
import Contact from '../components/Contact.vue';

useSeoMeta({
  title: 'Portfolio - Elie Lajoinie',
  ogTitle: 'Portfolio - Elie Lajoinie',
  description: 'Ce site est mon portfolio, et sert donc à répertorier tous mes projets. Aussi, je suis à la recherche d\'une alternance en développement.',
  ogDescription: 'Ce site est mon portfolio, et sert donc à répertorier tous mes projets. Aussi, je suis à la recherche d\'une alternance en développement.',
})

const activeTab = ref(1)

const direction = ref('')

watch(() => activeTab.value, (newValue, oldValue) => {
  if (newValue > oldValue) {
    direction.value = 'right'
  } else {
    direction.value = 'left'
  }
  window.scrollTo({ top: 0, behavior: 'smooth' })
})
</script>

<style lang="scss" scoped>
.arrowButton {
  @apply rounded-full bg-gray-800 shadow-md w-14 h-14 max-lg:w-10 max-lg:h-10 flex items-center justify-center;
}

</style>