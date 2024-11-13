<template>
    <div ref="skillsIntro">
        <Head title="Mes projets & expériences"/>
        <div class="flex flex-row w-full justify-center gap-5">
            <input type="text" v-model="search" placeholder="Rechercher un projet" class="w-1/3 p-2 rounded-lg border-2 border-gray-300 focus:border-blue-500 focus:outline-none"/>
                <select name="stacks" id="stacks-select" v-model="stack" class="p-2 rounded-lg border-2 border-gray-300 focus:border-blue-500 focus:outline-none">
                    <option value="" class="text-gray-400">Toute stack</option>
                    <option v-for="stack in stacks" :value="stack">{{ stack }}</option>
                </select>
        </div>
        <Project v-for="project in filteredProjects" @focus="focusedProject = project" :title="project.title" :bio="project.bio" :stacks="project.stacks" :link="project.link" :image="project.image"/>
        <div class="w-full justify-center text-center" v-if="filteredProjects.length == 0">
            <h1 class="text-xl font-bold text-gray-800">
                Aucun projet trouvé
            </h1>
        </div>
        <ProjectFocus @close="focusedProject = null" :project="focusedProject" v-if="focusedProject" />
    </div>
</template>

<script setup>
import Head from '../components/Head.vue';
import { ref, watch } from 'vue'
import { projects } from '../assets/data/projects.json'

const props = defineProps({
  direction: {
    type: { type: String, default: "right", validator: value => ['right', 'left'].includes(value) },
    required: true
  }
})

const search = ref('')
const skillsIntro = ref(null)
const focusedProject = ref(null)
const filteredProjects = ref(projects)
const stacks = ref([...new Set(projects.map(project => project.stacks).flat())])
const stack = ref('')


const filterProjects = (search, stack) => {
    filteredProjects.value = projects.filter(project => {
        const matchesSearch = search ? project.title.toLowerCase().includes(search.toLowerCase()) : true;
        
        const matchesStack = stack ? project.stacks.includes(stack) : true;
        
        return matchesSearch && matchesStack;
    });
}

watch(() => search.value, (newValue, oldValue) => {
    filterProjects(newValue, stack.value)
})

watch(() => stack.value, (newValue, oldValue) => {
    filterProjects(search.value, newValue)
})

onMounted(() => {
    props.direction === 'right' ? skillsIntro.value.classList.add('animate-slide-right') : skillsIntro.value.classList.add('animate-slide-left')
})
</script>