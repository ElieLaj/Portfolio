<template>
    <div>
    <div class="mx-auto px-4 sm:px-6 lg:px-8">
      <div class="bg-white shadow-xl rounded-lg overflow-hidden">
        <div class="flex lg:flex-row max-lg:flex-col max-lg:items-center max-lg:justify-center max-lg:text-center">
          <div class="px-6 py-8 sm:p-10 z-0 xl:w-2/3 lg:w-1/2 ">
            <h1 class="title">{{ name }}</h1>
            <h2 class="subtitle">{{ title }}</h2>
            <div class="text-container mt-4 group">
                <h2 class="text-title">Bio</h2>
                <p class="text">{{ bio }}</p>
            </div>
            <div class="mt-6" v-if="skills">
              <h3 class="text-title">Mes compétences</h3>
              <div class="skill-list">
                <span v-for="(logo, skill) in skills" :key="skill" class="main-skills">
                  <Icon :name="logo" class="text-primary mr-2 my-2" size="24px" />
                  {{ skill }}
                </span>
              </div>
            </div>
            <div class="mt-6" v-if="softSkills">
              <h3 class="text-title">Mes Softs-Skills</h3>
              <div class="skill-list">
                <span v-for="skill in softSkills" :key="skill" 
                class="secondary-skills">
                  {{ skill }}
                </span>
              </div>
            </div>
            <div class="mt-6" v-if="languages">
              <h3 class="text-title">Langues parlé</h3>
              <div class="skill-list">
                <span v-for="language in languages" :key="language" 
                class="tertiary-skills">
                {{ language.name }} - {{ language.level }}
                </span>
              </div>
            </div>
            <div class="mt-6" v-if="interests">
              <h3 class="text-title">Mes centres d'intérêts</h3>
              <div class="skill-list">
                <span v-for="interest in interests" :key="interest" 
                class="general-skills">
                {{ interest }}
                </span>
              </div>
            </div>
          </div>
          <div class="flex xl:w-1/3 lg:w-1/2 max-lg:w-full lg:justify-end max-lg:justify-center rounded-e-lg max-lg:bg-[url('/static/images/la_vague.jpg')] bg-cover">
                <img src="/static/images/moi-no-bg.png" alt="avatar" class="object-cover h-full lg:bg-[url('/static/images/la_vague.jpg')] bg-cover bg-center "/>
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
  languages: {
        type: Array,
        required: false
  },
  image: {
        type: String,
        required: false
  }
})

</script>