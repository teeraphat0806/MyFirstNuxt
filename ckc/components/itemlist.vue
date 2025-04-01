<template>
  <div class="flex justify-between">
    <p class="text-gray-500">{{title}}</p>
    <p class="text-xl">{{description}}</p>
  </div>
</template>

<script setup>
defineProps({ title: String, description: String });
</script>

<style lang="scss" scoped>
</style>