<template>
  <UDropdownMenu
    :items="items"
    :content="{
      align: 'start',
      side: 'bottom',
      sideOffset: 8,
    }"
    :ui="{
      content: 'w-48 bg-white text-white rounded-lg shadow-lg',
      
    }"
  >
  <div class="flex items-center">
    <div class="i-lucide-bell text-xl text-gray-600 hover:text-gray-800 cursor-pointer mr-4"></div>
    <img class="rounded-full h-10 w-10 mr-5" src="/img/rick.jpg" />
    <UButton
      class="text-white"
      :label="username"
      icon="i-mdi-chevron-down"
      color="ghost"
      variant="outline"
      @click="handleButtonClick"
    >
    </UButton>
  </div>
  </UDropdownMenu>
</template>

<script setup lang="ts">
import { ref } from "vue";
type MenuItem = {
  label: string;
  icon?: string;
  to?: string;
  click?: () => void;
};

const items = ref<MenuItem[]>([
  {
    label: "Profile",
    icon: "i-lucide-user",
    click: () => {},
  },
  {
    label: "Billing",
    icon: "i-lucide-credit-card",
    click: () => {},
  },
  {
    label: "Settings",
    icon: "i-lucide-cog",
    click: () => {},
  },
]);
const username = "rick";

function handleButtonClick() {
  
}
</script>

<style lang="scss" scoped>
</style>