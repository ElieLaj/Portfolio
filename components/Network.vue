<template>
    <div class="flex flex-row w-1/2 h-10 mx-auto shadow-lg" v-if="side === 'left'">
        <div class="flex flex-row p-4 h-full rounded-s-full bg-white items-center justify-center">
            <Icon :name="name" size="24"/>
        </div>
        <div class="flex flex-row w-full h-full items-center justify-center rounded-e-lg" :class="color">
            <a :href="link" class="flex flex-row font-medium text-lg items-center justify-center gap-2" :class="textColor">
            {{ pseudo }} <Icon name="uil:external-link-alt" :color="textColor"/>
            </a>
            
        </div>
    </div>
    <div class="flex flex-row w-1/2 h-10 mx-auto shadow-lg" v-else>
        <div class="flex flex-row w-full h-full items-center justify-center rounded-s-lg" :class="color">
            <a :href="link" class="flex flex-row font-medium text-lg items-center justify-center gap-2" :class="textColor">
            {{ pseudo }} <Icon name="uil:external-link-alt" :color="textColor"/>
            </a>
        </div>
        <div class="flex flex-row p-4 h-full rounded-e-full bg-white items-center justify-center">
            <Icon :name="name" size="24"/>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    name: {
        type: String,
        required: true,
    },
    link: {
        type: String,
        required: true,
    },
    pseudo: {
        type: String,
        required: true,
    },
    side: {
        type: String,
        default: 'left',
        validator: value => ['right', 'left'].includes(value),
        required: false,
    },
    color: {
        type: String,
        default: 'bg-gray-800',
        required: false,
    },
    textColor: {
        type: String,
        default: 'text-white',
        required: false,
    }
})

</script>