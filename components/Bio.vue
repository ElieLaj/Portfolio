<template>
    <div>
    <div class="mx-auto px-4 sm:px-6 lg:px-8">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="sm:flex sm:items-center sm:justify-between">
          <div class="px-6 py-8 sm:p-10 z-0 w-2/3">
            <h1 class="text-5xl font-bold text-gray-900">{{ name }}</h1>
            <h2 class="text-3xl font-medium text-gray-700">{{ title }}</h2>
            <div class="mt-4">
                <h2 class="text-2xl font-medium text-gray-900">Bio</h2>
                <p class="text-gray-700 text-lg">{{ bio }}</p>
            </div>
            <div class="mt-6" v-if="skills">
              <h3 class="text-2xl font-medium text-gray-900">Mes compétences</h3>
              <div class="mt-3 flex flex-wrap gap-2">
                <span v-for="skill in skills" :key="skill" class="bg-gray-800 text-white hover:bg-blue-600 duration-200 px-3 py-1 rounded-full text-md">{{ skill }}</span>
              </div>
            </div>
            <div class="mt-6" v-if="softSkills">
              <h3 class="text-2xl font-medium text-gray-900">Mes Softs-Skills</h3>
              <div class="mt-3 flex flex-wrap gap-2">
                <span v-for="skill in softSkills" :key="skill" class="bg-gray-200 text-gray-700 hover:bg-gray-800 hover:text-white duration-200 px-3 py-1 rounded-full text-md">{{ skill }}</span>
              </div>
            </div>
            <div class="mt-6" v-if="interests">
              <h3 class="text-2xl font-medium text-gray-900">Mes centres d'intérêts</h3>
              <div class="mt-3 flex flex-wrap gap-2">
                <span v-for="interest in interests" :key="interest" class="bg-gray-200 text-gray-700 hover:bg-gray-800 hover:text-white duration-200 px-3 py-1 rounded-full text-md">{{ interest }}</span>
              </div>
            </div>
          </div>
          <div class="flex h-full w-1/3 justify-center bg-gray-800 rounded-lg bg-[url('/assets/images/la_vague.jpg')] bg-cover bg-center">
                <img src="/assets/images/moi-no-bg.png" alt="avatar" class="w-full"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  name: {
    type: String,
    required: true
  },
  bio: {
        type: String,
        required: true
  },
  skills: {
        type: Array,
        required: false
  },
  softSkills: {
        type: Array,
        required: false
  },
  interests: {
        type: Array,
        required: false
  },
  image: {
        type: String,
        required: false
  }
})

</script>