<template>
    <Teleport to="body">
        <Transition name="modal-outer">
            <div v-show="isModalActive" class="bg-black w-full absolute h-screen bg-opacity-30 flex justify-center px-8 top-0 left-0">
                <Transition name="modal-inner">
                    <div v-if="isModalActive" class="p-4 bg-white text-black self-start mt-32 max-w-screen-sm">
                        <slot />

                        <button class="text-white mt-8 bg-weather-primary hover:bg-weather-primary py-2 px-6" @click="$emit('closeModal')">
                            close
                        </button>
                    </div>
                </Transition>
            </div>
        </Transition>
    </Teleport>
</template>

<script setup lang="ts">
defineEmits(['closeModal'])
defineProps({
    isModalActive: {
        type: Boolean,
        default: false
    }
})
</script>

<style scoped>
.modal-outer-enter-active,
.modal-outer-leave-active {
    transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-outer-enter-from,
.modal-outer-leave-to {
    opacity: 0;
}

.modal-inner-enter-active {
    transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.15s;
}

.modal-inner-leave-active {
    transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-inner-enter-from {
    opacity: 0;
    transform: scale(0.8);
}

.modal-inner-leave-to {
    transform: scale(0.8);
}
</style>
