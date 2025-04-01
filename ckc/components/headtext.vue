<template>
    <div class="flex items-center space-x-2">
            <UButton
              :class="`${color}`"
              :icon="`${icon}`"
              color="white"
              variant="ghost"
            />
            <p :class="`text-2xl ${color}`">{{title}}</p>
    </div>
</template>

<script setup>
defineProps({
    title: String,
    color: {
        type: String,   
        default: 'text-green-500'
    },
    icon: {
        type: String,
        default: 'i-heroicons-calendar'
    }
})
</script>

<style lang="scss" scoped>

</style>