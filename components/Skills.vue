<template>
    <div ref="skillsIntro">
        <Head title="Mes projets & expériences"/>
        <div class="w-full text-center">
            <input type="text" v-model="search" placeholder="Rechercher un projet" class="w-1/2 p-2 mx-auto rounded-lg border-2 border-gray-300 focus:border-blue-500 focus:outline-none"/>
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
const hiddenProjects = ref([])

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('animate-fade-in')
        }
        else {
            entry.target.classList.remove('animate-fade-in')
        }
    })
})

watch(() => hiddenProjects.value, (newValue, oldValue) => {
    if (newValue) {
        observer.observe(newValue)
    }
})

watch(() => search.value, (newValue, oldValue) => {
    if (newValue !== '') {
        filteredProjects.value = projects.filter(project => 
            project.title.toLowerCase().includes(newValue.toLowerCase()) ||
            project.bio.toLowerCase().includes(newValue.toLowerCase()) ||
            project.stacks.some(stack => stack.toLowerCase().includes(newValue.toLowerCase()))
        )
    } else {
        filteredProjects.value = projects
    }
})

onMounted(() => {
    props.direction === 'right' ? skillsIntro.value.classList.add('animate-slide-right') : skillsIntro.value.classList.add('animate-slide-left')
    hiddenProjects.value = document.querySelectorAll('.hiddenProject')
    if (hiddenProjects.value && hiddenProjects.value.length > 0) {
        hiddenProjects.value.forEach(project => observer.observe(project))
    }
})
</script>