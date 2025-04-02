<template>
    <div class="flex items-center space-x-2">
        <UButton
          :class="[color, custom]"
          :icon="icon"
          color="white"
          variant="ghost"
        />
        <p :class="['text-2xl', color]">{{ title }}</p>
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
    },
    custom: {
        type: String,
        default: ''
    }
});
</script>

<style lang="scss" scoped>
</style>