<template>
    <div ref="homeIntro">
      <Head title="Bienvenue sur mon portfolio" />
      <Bio :name="name" :title="title" :bio="bio" :skills="skills" :softSkills="softSkills" :interests="interests" :languages="languages" />
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
const title = 'Etudiant en 3ème année - Futur Développeur Fullstack / Application'
const bio = 'Actuellement en formation à Sup de Vinci en 3ème année, je suis à la recherche d\'une alternance ou d\'un stage. Curieux, dynamique et créatif, je suis passionné par le développement web et d\'applications. J\'aime découvrir de nouvelles technologies et les mettre en pratique dans des projets personnels ou professionnels.'
const skills = {
  'Vue.js': 'logos-vue',
  'React': 'devicon-react',
  'Angular': 'devicon-angularjs',
  'TypeScript': 'devicon-typescript',
  'Node.js': 'devicon:nodejs',
  'Spring Boot': 'devicon-spring',
  'Java': 'logos-java',
  'Django': 'vscode-icons:file-type-django',
  'Python': 'logos-python',
  'MongoDB': 'devicon:mongodb',
  'PostgreSQL': 'logos-postgresql',
  'Linux': 'devicon:linux',
  'Git': 'devicon-git',
};
const softSkills = ['Travail d\'équipe', 'Rigoureux', 'Gestion de projet', 'Autonome', 'Polyvalent']
const interests = ['Pâtisserie', 'Langues étrangères', 'Mangas', 'Informatique', 'Apprendre', 'Jeux vidéo']
const languages = [ { name: 'Français', level: 'C2' }, { name: 'Anglais', level: 'C1' }, { name: 'Espagnol', level: 'B1' }, { name: 'Japonais', level: 'A2' } ]

onMounted(() => {
  const directionClass = props.direction === 'right' ? 'animate-slide-right' : 'animate-slide-left'
  homeIntro.value.classList.add(directionClass)
})
</script>