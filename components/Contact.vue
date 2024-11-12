<template>
    <div class="w-full" ref="contactIntro">
     <Head title="Contactez-moi" />
     <div class="flex flex-col gap-8">
        <h1 class="text-4xl font-bold text-center">Mes réseaux</h1>
        <Network v-for="(network, index) in networks" :key="index" :name="network.name" :link="network.link" :pseudo="network.pseudo"
            :color="network.color" :textColor="network.textColor" :side="index % 2 === 0 ? 'left' : 'right'"
        />
     </div>
    </div>    
</template>


<script setup>
import Head from '../components/Head.vue'
import Network from '../components/Network.vue'
const contactIntro = ref(null)

const props = defineProps({
    direction: {
        type: String,
        default: 'right',
        validator: value => ['right', 'left'].includes(value),
        required: true,
    }
})

const networks = [
    {
        name: 'devicon:linkedin',
        link: 'https://www.linkedin.com/in/elie-lajoinie-37b05b231/',
        pseudo: 'Elie LAJOINIE',
        color: 'bg-blue-600',
        textColor: 'text-white'
    },
    {
        name: 'skill-icons:github-dark',
        link: 'https://github.com/ElieLaj',
        pseudo: 'ElieLaj',
    },
    {
        name: 'logos:google-gmail',
        link: 'mailto:elielajoiniepro@gmail.com',
        pseudo: 'elielajoiniepro@gmail.com',
        color: 'bg-red-600',
        textColor: 'text-white'
    }
]

onMounted(() => {
    const directionClass = props.direction === 'right' ? 'animate-slide-right' : 'animate-slide-left'
    contactIntro.value.classList.add(directionClass)
})

</script>