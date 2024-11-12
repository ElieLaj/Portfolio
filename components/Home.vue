<template>
    <div ref="homeIntro">
      <Head title="Bienvenue sur mon portfolio" />
      <Bio :name="name" :title="title" :bio="bio" :skills="skills" :softSkills="softSkills" :interests="interests" />
      <Aspiration/>
    </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import Head from '../components/Head.vue'
import Bio from './Bio.vue'

const props = defineProps({
  direction: {
    type: String,
    default: 'right',
    validator: value => ['right', 'left'].includes(value),
    required: true,
  }
})

const homeIntro = ref(null)

const name = 'Elie LAJOINIE'
const title = 'Développeur Full-Stack / Application'
const bio = 'Actuellement en formation chez Sup de Vinci en 3ème année, je suis à la recherche d\'une alternance. Curieux dynamique et créatif, je suis passionné par le développement web et application. J\'aime découvrir de nouvelles technologies et les mettre en pratique dans des projets personnels ou professionnels.'
const skills = ['Vue.js', 'React', 'Node.js', 'Django', 'Python', 'MongoDB', 'PostgreSQL', 'Linux']
const softSkills = ['Travail d\'équipe', 'Rigoureux', 'Gestion de projet', 'Autonome', 'Polyvalent']
const interests = ['Pâtisserie', 'Langues étrangères', 'Mangas', 'Informatique', 'Apprendre']

onMounted(() => {
  const directionClass = props.direction === 'right' ? 'animate-slide-right' : 'animate-slide-left'
  homeIntro.value.classList.add(directionClass)
})
</script>