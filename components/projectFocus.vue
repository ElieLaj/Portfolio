<template>
  <div class="fixed inset-0 z-50 flex items-center justify-center">
    <div class="absolute inset-0 bg-black bg-opacity-40 backdrop-blur-md" @click="$emit('close')"></div>

    <div class="relative bg-white shadow-xl rounded-lg overflow-hidden w-11/12 sm:w-3/4 lg:w-1/2 p-8 flex flex-col items-center space-y-6 z-50">

      <button @click="$emit('close')" class="absolute top-4 right-4 text-gray-800 hover:text-gray-900 text-lg hover:text-2xl duration-300">
        ✕
      </button>

      <a :href="link ? link : '#'" target="_blank" class="text-4xl font-bold text-gray-900 cursor-pointer underscore">
        {{ title }}
      </a>

      <a :href="link ? link : '#'" target="_blank" class="relative group w-full">
        <img :src="`/_nuxt/assets/images/` + image" alt="avatar" class="rounded-lg w-full h-auto cursor-pointer group-hover:opacity-75 transition-opacity duration-150" />
      </a>

      <div v-if="stacks" class="w-full text-center">
        <h3 class="text-xl font-medium text-gray-900">Stacks</h3>
        <div class="flex flex-wrap justify-center gap-2 mt-3">
          <span v-for="stack in stacks" :key="stack" class="bg-gray-800 text-white px-3 py-1 rounded-full text-sm">{{ stack }}</span>
        </div>
      </div>

      <div class="text-center w-full">
        <h2 class="text-xl font-medium text-gray-900">Résumé</h2>
        <p class="text-gray-600">{{ more ? more : bio }}</p>
      </div>

      <a :href="'/assets/other/'+doc+'.pdf'" download="CV Lajoinie Elie.pdf" class="self-center text-center w-1/2 py-3 bg-gray-200 text-gray-700 rounded-full text-sm">Télécharger {{ docTitle }}</a>

    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(['close']);

const props = defineProps({
  project: {
    type: Object,
    required: true
  }
});

const { title, bio, stacks, link, image, more, doc, docTitle } = props.project;
</script>

<style scoped>
.fixed {
  backdrop-filter: blur(8px);
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