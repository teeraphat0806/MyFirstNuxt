<template>
  <aside
    class="group hidden md:block md:absolute top-0 left-0 h-full w-18 hover:w-68 transition-all duration-400 ease-in-out bg-gradient-to-b from-[#40B59F] to-[#F5CC3B] text-white p-2 z-10"
  >
    <div class="flex p-1">
      <div
        class="mt-2 h-9 w-9 rounded-full ml-2 animate-pulse bg-gray-400 mr-2 group-hover:h-9 w-9 hover:duration-300 ease-in-out"
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
          :to="data.nav"
          class="text-gray-200 hover:text-white hover: px-3 py-2 rounded flex text-xl"
        style="hover: text-shadow: 0 0 3px #fff, 0 0 5px #fff;"
        >
          <UButton
            class="text-white mr-5"
            :icon="`${data.icon}`"
            color="white"
            variant="ghost"
            :ui="{ icon: { base: 'w-10 h-10' } }"
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
</template>

<script setup lang="ts">
const datas = [
  { icon: "i-mdi-plus-box-outline", title: "สร้างรายการ", nav: "/documents", id: 1 },
  { icon: "i-mdi-folder-outline", title: "รายการทั้งหมด", nav: "/documents", id: 2 },
  { icon: "i-mdi-pencil-outline", title: "จัดการชุดเอกสาร", nav: "/documents", id: 3 },
  { icon: "i-mdi-view-dashboard-outline", title: "ข้อมูลสถิติ", nav: "/documents", id: 4 },
  { icon: "i-mdi-file-document-outline", title: "รายงาน", nav: "/documents", id: 5 },
  { icon: "i-mdi-book-open-outline", title: "คู่มือการใช้งาน", nav: "/documents", id: 6 },
  { icon: "i-mdi-cog-outline", title: "การตั้งค่า", nav: "/documents", id: 7 },
];
</script>

<style lang="scss" scoped>
aside {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  z-index: 10; /* Sidebar อยู่เหนือ Header */
}
</style>