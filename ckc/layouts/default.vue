<template>
  <div class="flex min-h-screen">
    <!-- Sidebar -->

    <aside
      class="group  hidden md:block w-20 hover:w-68 transition-all duration-400 ease-in-out bg-gradient-to-b from-green-400 via-green-400 to-yellow-300 text-white p-4"
    >
      <div class="flex p-1 overflow-hidden max-w-0 opacity-0 group-hover:max-w-full group-hover:opacity-100 transition-all duration-300 ease-in-out whitespace-nowrap">
        <div
          class="h-15 w-15 rounded-full animate-pulse bg-gray-400 mr-2"
        ></div>
        <div class="grid-cols-1 font-semibold text-lx ">
          <h2>ระบบตรวจติดตาม</h2>
          <h2>การให้ความช่วยเหลือ</h2>
        </div>
      </div>

      <nav class="flex flex-col space-y-2 mt-5">
        <div v-for="data in datas" :key="data.id">
          <NuxtLink
            to="/"
            class="hover:bg-gray-700 px-3 py-2 rounded flex text-xl"
          >
            <UButton
              class="text-white mr-5"
              :icon="`${data.icon}`"
              color="white"
              variant="ghost"
            />
            <p class="overflow-hidden max-w-0 opacity-0 group-hover:max-w-full group-hover:opacity-100 transition-all duration-300 ease-in-out whitespace-nowrap">{{ data.title }}</p>
          </NuxtLink>
        </div>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 p-6 bg-gray-100 overflow-auto">
      <slot />
    </main>
  </div>
</template>

<script setup>
const datas = [
  { icon: "i-mdi-plus-box-outline", title: "สร้างรายการ", id: 1 },
  { icon: "i-mdi-folder-outline", title: "รายการทั้งหมด", id: 2 },
  { icon: "i-mdi-pencil-outline", title: "จัดการชุดเอกสาร", id: 3 },
  { icon: "i-mdi-view-dashboard-outline", title: "ข้อมูลสถิติ", id: 4 },
  { icon: "i-mdi-file-document-outline", title: "รายงาน", id: 5 },
  { icon: "i-mdi-book-open-outline", title: "คู่มือการใช้งาน", id: 6 },
  { icon: "i-mdi-cog-outline", title: "การตั้งค่า", id: 7 },
];
</script>

<style lang="scss" scoped>
</style>