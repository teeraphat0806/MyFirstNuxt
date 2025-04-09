<template>
  <div class="bg-[#40B59F] p-3.5 flex justify-between z-0 relative md:ml-15">
    <div class="text-xl text-white font-bold flex">
      <UButton
        v-if="pageTitle != 'หน้าหลัก'"
        icon="i-lucide-chevron-left"
        class="text-white"
        color="white"
        variant="ghost"
        @click="goBack"
      />
      <div class="mt-1 ml-5">
        {{ pageTitle }}
      </div>
    </div>
    <div class="flex justify-end">
      <UButton
        icon="i-mdi-bell"
        class="text-white"
        color="white"
        variant="ghost"
      />
      <dropdown />
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRoute, useRouter } from "vue-router";
import { computed } from "vue";

const route = useRoute();
const router = useRouter();
const pageTitle = computed(() => route.meta.title || "");

function goBack() {
  if (window.history.length > 1) {
    router.back();
  } else {
    router.push("/");
  }
}
</script>

<style lang="scss" scoped>
div {
  position: relative;
  z-index: 0; /* Header อยู่ต่ำกว่า Sidebar */
}
</style>