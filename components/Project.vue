<template>
  <div class="my-8">
    <div class="mx-auto px-4 sm:px-6 lg:px-8">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="sm:flex sm:items-center sm:justify-between">
          <div class="flex flex-col px-6 py-8 sm:p-10 h-full">
            <div class="flex w-fit">
              <a :href="link ? link : '#'" target="_blank" class="underscore">
                <h1 class="text-4xl font-bold text-gray-900 cursor-pointer">{{ title }}</h1>
              </a>
            </div>
            <div class="mt-6" v-if="stacks">
              <h3 class="text-xl font-medium text-gray-900">Stacks</h3>
              <div class="mt-3 flex flex-wrap gap-2">
                <span v-for="stack in stacks" :key="stack" class="bg-gray-800 text-white px-3 py-1 rounded-full text-sm">{{ stack }}</span>
              </div>
            </div>
            <div class="mt-4">
              <h2 class="text-xl font-medium text-gray-900">Résumé</h2>
              <p class="text-gray-600">{{ bio }}</p>
            </div>
            <a class="pt-6 text-xl font-medium text-gray-900 cursor-pointer" @click="emitFocus()">En savoir plus</a>
          </div>
          <div class="flex h-full justify-center bg-gray-800 rounded-lg image-div relative" v-if="image">
            <a :href="link ? link : '#'" target="_blank" class="image-link group">
              <img :src="`/_nuxt/assets/images/` + image" alt="avatar" class="cursor-pointer"/>
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
.image-link:hover {
    @apply blur-sm duration-150 ;
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