<template>
    <div class="network-container" v-if="side === 'left'">
        <div class="right-logo logo ">
            <Icon :name="name" size="24"/>
        </div>
        <div class="network-text right-network-text" :class="color">
            <a :href="link" class="link underscore" :class="textColor">
            {{ pseudo }} <Icon name="uil:external-link-alt" :color="textColor"/>
            </a>
        </div>
    </div>
    <div class="network-container" v-else>
        <div class="network-text left-network-text" :class="color">
            <a :href="link" class="link underscore" :class="textColor">
                {{ pseudo }} <Icon name="uil:external-link-alt" :color="textColor"/>
            </a>
        </div>
        <div class="left-logo logo">
            <Icon :name="name" size="24"/>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.network-container {
    @apply flex flex-row lg:w-1/2 max-lg:w-2/3 h-12 mx-auto shadow-lg;
    .logo {
        @apply flex flex-row p-4 h-full bg-white items-center justify-center;
    }
    .right-logo {
        @apply rounded-s-full;
    }
    .left-logo {
        @apply rounded-e-full;
    }
    .network-text {
        @apply flex flex-row w-full h-full items-center justify-center overflow-hidden text-ellipsis ;
        .link {
            @apply flex flex-row font-medium text-lg max-lg:text-sm items-center justify-center gap-2;
        }
    }
    .right-network-text {
        @apply rounded-e-lg;
    }
    .left-network-text {
        @apply rounded-s-lg;
    }
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
  background-color: white;
  transition: width 0.3s ease;
}

.underscore:hover::after {
  width: 100%;
}
</style>

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

