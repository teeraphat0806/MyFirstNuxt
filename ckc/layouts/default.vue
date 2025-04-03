<template>
  <div class="flex min-h-screen">
    <!-- Sidebar -->

    <aside
      class="group hidden md:block w-24 hover:w-68 transition-all duration-400 ease-in-out bg-gradient-to-b from-green-400 via-green-400 to-yellow-300 text-white p-4"
    >
      <div class="flex p-1">
        <div
          class="h-10 w-10 rounded-full ml-2 animate-pulse bg-gray-400 mr-2 group-hover:h-15 w-15 hover:duration-300 ease-in-out"
        ></div>
        <div
          class="grid-cols-1 font-semibold text-lx overflow-hidden max-w-0 opacity-0 group-hover:max-w-full group-hover:opacity-100 transition-all duration-300 ease-in-out whitespace-nowrap"
        >
          <h2>ระบบตรวจติดตาม</h2>
          <h2>การให้ความช่วยเหลือ</h2>
        </div>
      </div>

      <nav class="flex flex-col space-y-2 mt-5">
        <div v-for="data in datas" :key="data.id">
          <NuxtLink
            to="/documents"
            class="hover:bg-gray-700 px-3 py-2 rounded flex text-xl"
          >
            <UButton
            :v-if="data.title !== 'หน้าหลัก'"
              class="text-white mr-5"
              :icon="`${data.icon}`"
              color="white"
              variant="ghost"
              :ui="{
                icon: { base: 'w-10 h-10' }, // 👈 ปรับขนาด icon ตรงนี้เลย!
              }"
            />

            <p
              class="overflow-hidden max-w-0 opacity-0 group-hover:max-w-full group-hover:opacity-100 transition-all duration-300 ease-in-out whitespace-nowrap"
            >
              {{ data.title }}
            </p>
          </NuxtLink>
        </div>
      </nav>
    </aside>

    <!-- Main Content -->
    <div class="w-full grid-col">
      <div class="bg-green-400 p-3 flex justify-between">
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
      <main class="flex-1 p-6 bg-gray-100 overflow-auto">
        <slot />
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRoute, useRouter } from "vue-router";
import { computed, watchEffect } from "vue";

const datas = [
  { icon: "i-mdi-plus-box-outline", title: "สร้างรายการ", id: 1 },
  { icon: "i-mdi-folder-outline", title: "รายการทั้งหมด", id: 2 },
  { icon: "i-mdi-pencil-outline", title: "จัดการชุดเอกสาร", id: 3 },
  { icon: "i-mdi-view-dashboard-outline", title: "ข้อมูลสถิติ", id: 4 },
  { icon: "i-mdi-file-document-outline", title: "รายงาน", id: 5 },
  { icon: "i-mdi-book-open-outline", title: "คู่มือการใช้งาน", id: 6 },
  { icon: "i-mdi-cog-outline", title: "การตั้งค่า", id: 7 },
];
const route = useRoute();
const router = useRouter(); // Use useRouter for navigation
const pageTitle = computed(() => route.meta.title || "");

// Watch for route changes to debug if needed
watchEffect(() => {
  console.log("Current route meta:", route.meta);
});

function goBack() {
  if (window.history.length > 1) {
    router.back(); // Use router.back() for navigation
  } else {
    router.push("/"); // Use router.push() for fallback navigation
  }
}
</script>

<style lang="scss" scoped>
</style>