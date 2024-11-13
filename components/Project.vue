<template>
  <div class="my-8 max-lg:mx-4 transition-all duration-100 animate-fade-in">
    <div class="mx-auto px-4 sm:px-4 lg:px-8">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="flex max-lg:flex-col items-center justify-between h-fit">
          <div class="flex flex-col px-6 py-8 sm:p-10 h-full group max-lg:items-center max-lg:justify-between max-lg:text-center">
            <div class="flex w-fit">
              <a :href="link ? link : '#'" target="_blank" class="underscore">
                <h1 class="title cursor-pointer">{{ title }}</h1>
              </a>
            </div>
            <div class="mt-6" v-if="stacks">
              <h3 class="text-title">Stacks</h3>
              <div class="skill-list">
                <span v-for="stack in stacks" :key="stack" class="main-skills">{{ stack }}</span>
              </div>
            </div>
            <div class="mt-4 group">
              <h2 class="text-title">Résumé</h2>
              <p class="text">{{ bio }}</p>
            </div>
            <a class="mt-6 text-xl max-lg:text-lg font-medium text-gray-900 cursor-pointer duration-200 rounded-full p-4 max-lg:py-2 max-lg:px-3 bg-gray-200 group-hover:bg-gray-800 group-hover:text-white w-fit" @click="emitFocus()">
            En savoir plus
            </a>
          </div>
          <div class="flex h-full max-lg:mb-5 justify-center bg-gray-800 rounded-lg duration-150 max-w-1/2 max-lg:w-3/4 relative group" v-if="image">
            <a :href="link ? link : '#'" target="_blank" class="image-link duration-150">
              <Icon size="32" name="quill:link-out" class="absolute invisible right-1/2 top-1/2 translate-x-1/2 text-white group-hover:visible z-10 duration-100"/>
              <img :src="`/images/` + image" alt="avatar" class="cursor-pointer group-hover:blur-sm duration-200"/>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const emit = defineEmits(['focus']);

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  bio: {
    type: String,
    required: true
  },
  stacks: {
    type: Array,
    required: false
  },
  link: {
    type: String,
    required: false
  },
  image: {
    type: String,
    required: false
  }
});

const emitFocus = () => {
  console.log('emit focus')
  emit('focus')
}
</script>

<style lang="scss" scoped>

.underscore {
  position: relative;
  text-decoration: none;
}

.underscore::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -2px;
  width: 0;
  height: 2.5px;
  background-color: black;
  transition: width 0.3s ease;
}

.underscore:hover::after {
  width: 100%;
}
</style>