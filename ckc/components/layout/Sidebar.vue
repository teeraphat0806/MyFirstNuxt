<template>
  <aside
    class="group hidden md:block fixed top-0 left-0 h-screen w-18 hover:w-68 transition-all duration-400 ease-in-out bg-gradient-to-b from-[#40B59F] to-[#F5CC3B] text-white z-10 overflow-y-auto"
  >
    <div class="flex p-3">
      <div
        class="mt-2 h-9 w-9 rounded-full ml-2 animate-pulse bg-gray-400 mr-2 group-hover:h-9 w-9 hover:duration-300 ease-in-out"
      ></div>
      <div
        class="grid-cols-1 font-medium text-[1.1rem] overflow-hidden max-w-0 opacity-0 group-hover:max-w-full group-hover:opacity-100 transition-all duration-300 ease-in-out whitespace-nowrap"
      >
        <p>ระบบตรวจติดตาม</p>
        <p>การให้ความช่วยเหลือ</p>
      </div>
    </div>
    <hr class="w-full overflow-auto space-x-0" />
    <nav class="flex flex-col space-y-2 mt-5 p-2">
      <div v-for="data in datas" :key="data.id">
        <NuxtLink
          :to="data.nav"
          class="text-gray-200 hover:text-white px-3 py-1 rounded flex text-xl"
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
  { icon: "ic:round-plus", title: "สร้างรายการ", nav: "/documents", id: 1 },
  { icon: "material-symbols:folder-outline", title: "รายการทั้งหมด", nav: "/documents", id: 2 },
  { icon: "solar:document-add-outline", title: "จัดการชุดเอกสาร", nav: "/documents", id: 3 },
  { icon: "uil:statistics", title: "ข้อมูลสถิติ", nav: "/documents", id: 4 },
  { icon: "mingcute:document-line", title: "รายงาน", nav: "/documents", id: 5 },
  { icon: "iconoir:book", title: "คู่มือการใช้งาน", nav: "/documents", id: 6 },
  { icon: "clarity:cog-line", title: "การตั้งค่า", nav: "/documents", id: 7 },
];
</script>

<style lang="scss" scoped>
aside {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  z-index: 10; /* Sidebar อยู่เหนือ Header */
}
</style>