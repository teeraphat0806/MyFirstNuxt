<template>
  <div class="flex min-h-screen">
    <Sidebar />
    <div class="w-full grid-col">
      <Header />
      <main class=" flex-1 p-6 md:ml-15 bg-white overflow-auto z-0 relative ">
        <slot />
      </main>
    </div>
  </div>
</template>

<script setup>
import Sidebar from '~/components/layout/Sidebar.vue';
import Header from '~/components/layout/Header.vue';
</script>

<style scoped>
/* Add your styles here */
</style>