<template>
  <div class="my-8 opacity-0 transition-all duration-100 hiddenProject">
    <div class="mx-auto px-4 sm:px-6 lg:px-8">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="sm:flex sm:items-center sm:justify-between h-fit">
          <div class="flex flex-col px-6 py-8 sm:p-10 h-full">
            <div class="flex w-fit">
              <a :href="link ? link : '#'" target="_blank" class="underscore">
                <h1 class="text-4xl font-bold text-gray-900 cursor-pointer">{{ title }}</h1>
              </a>
            </div>
            <div class="mt-6" v-if="stacks">
              <h3 class="text-xl font-medium text-gray-900">Stacks</h3>
              <div class="mt-3 flex flex-wrap gap-2">
                <span v-for="stack in stacks" :key="stack" class="bg-gray-800 text-white px-3 py-1 rounded-full text-sm hover:bg-blue-600 duration-200">{{ stack }}</span>
              </div>
            </div>
            <div class="mt-4 group">
              <h2 class="text-xl font-medium text-gray-900">Résumé</h2>
              <p class="text-gray-600 group-hover:text-lg group-hover:text-gray-900 duration-300">{{ bio }}</p>
            </div>
            <a class="mt-6 text-xl font-medium text-gray-900 cursor-pointer duration-200 hover:rounded-full hover:p-3 hover:bg-gray-200 w-fit" @click="emitFocus()">En savoir plus</a>
          </div>
          <div class="flex h-full justify-center bg-gray-800 rounded-lg duration-150 image-div relative group" v-if="image">
            <a :href="link ? link : '#'" target="_blank" class="image-link duration-150">
              <Icon size="32" name="quill:link-out" class="absolute invisible right-1/2 top-1/2 translate-x-1/2 text-white group-hover:visible z-10 duration-100"/>
              <img :src="`/_nuxt/assets/images/` + image" alt="avatar" class="cursor-pointer group-hover:blur-sm duration-200"/>
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
.image-div {
    max-width: 50%;
}

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