<template>
  <UApp>
    <!-- Section: Header and Step Icons -->
    <div class="flex flex-col items-center gap-4 p-4">
      <div class="flex flex-wrap justify-center gap-4 ">
        <headtext title="ปีงบประมาณ 2567" icon="i-heroicons-calendar" />
        <headtext title="ด้านการดำรงชีพ" icon="i-heroicons-paper-airplane" />
        <headtext title="จังหวัดเลย" icon="i-mdi-database" />
      </div>

      <div class="flex flex-wrap justify-center gap-4 ">
        <div
          v-for="item in items"
          :key="item.id"
          class="flex flex-col items-center gap-2 w-20"
        >
          <UButton
            :class="[
              'w-12 h-12 rounded-full flex items-center justify-center',
              activeId === item.id
                ? 'bg-gradient-to-br from-green-900 via-green-800 to-green-700 text-white'
                : 'bg-gray-200 text-gray-500',
            ]"
            :icon="item.icon"
            variant="solid"
            @click="activeId = item.id"
          />
          <p class="text-xs text-center text-green-500">{{ item.title }}</p>
        </div>
      </div>
    </div>

    <!-- Section: Cards Layout -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-4">
      <!-- Card: Book Info -->
      <UCard class="w-full">
        <div class="space-y-2">
          <headtext title="ข้อมูลหนังสือ" icon="i-mdi-book-open-variant" />
          <div v-for="book in books" :key="book.id">
            <itemlist :title="book.title" :description="book.description" />
          </div>
        </div>
      </UCard>

      <!-- Card: Harmful Info -->
      <UCard class="w-full">
        <div class="space-y-2">
          <headtext title="ข้อมูลภัย" icon="i-mdi-home-flood" />
          <div v-for="harm in harmful" :key="harm.id">
            <itemlist :title="harm.title" :description="harm.description" />
          </div>
        </div>
      </UCard>

      <!-- Card: Help Info -->
      <UCard class="w-full">
        <div class="space-y-2">
          <headtext title="รายการช่วยเหลือ" icon="i-mdi-handshake" />
          <div v-for="help in helps" :key="help.id">
            <itemlist :title="help.title" :description="help.description" />
          </div>
        </div>
      </UCard>

      <!-- Card: Place Info -->
      <UCard class="w-full">
        <div class="space-y-2">
          <headtext title="สถานที่ดำเนินการ" icon="i-mdi-map-marker" />
          <div v-for="place in places" :key="place.id">
            <itemlist :title="place.title" :description="place.description" />
          </div>
        </div>
      </UCard>

      <!-- Card: Pay Info -->
      <UCard class="md:max-w-2xl lg:max-w-310 xl:w-200">
        <div class="space-y-2">
          <headtext title="ค่าใช้จ่าย" icon="i-mdi-cash-multiple" />
          <div v-for="pay in pays" :key="pay.id">
            <itemlist :title="pay.title" :description="pay.description" />
          </div>
          <hr class="border-t border-black my-2" />
          <itemlist :title="allpay.title" :description="allpay.description" />
        </div>
      </UCard>
    </div>
  </UApp>
</template>


<script setup lang="ts">

import { ref } from "vue";

const activeId = ref(null);
const items = [
  { title: "ประกาศเขตการให้ความช่วยเหลือ", id: 1, icon: "i-mdi-bullhorn" },
  { title: "เบิกเงินจากคลัง", id: 2, icon: "i-mdi-cash" },
  {
    title: "สั่งเอกสารชดใช้เงินทดรองรายการ",
    id: 3,
    icon: "i-mdi-file-document",
  },
  {
    title: "สั่งเอกสารชดใช้เงินทดรองรายการ",
    id: 4,
    icon: "i-mdi-flag-checkered",
  },
  { title: "รมว.มท.เห็นชอบ", id: 5, icon: "i-mdi-pill" },
  { title: "สั่งกรม บัญชีกลาง", id: 6, icon: "i-mdi-send" },
  { title: "หลักการกรมบัญชีกลาง", id: 7, icon: "i-mdi-domain" },
];
const books = [
  { title: "ครั้งที่", description: "1", id: 1 },
  { title: "เลขที่หนังสือจังหวัด", description: "ลย 0021 / 9708", id: 2 },
  { title: "ชั้นความเร็ว", description: "ด่วนที่สุด", id: 3 },
  { title: "เลขที่เอกสาร GFMIS", description: "3600000365", id: 4 },
  { title: "วันที่เอกสาร GFMIS", description: "16/10/2567", id: 5 },
  { title: "วงเงิน", description: "HR (ปกติ)", id: 6 },
];
const harmful = [
  { title: "ห้วงเกิดภัย", description: "8/5/2567", id: 1 },
  { title: "วันที่ประกาศภัย", description: "18/6/2567", id: 2 },
  { title: "ขอขยายเวลาถึง", description: "28/7/2567", id: 3 },
  { title: "ประวัติการบันทึกการประชุม", description: "ดูประวัติ", id: 4 },
];
const helps = [
  { title: "หลักเกณฑ์", description: "5.1.13 ค่าจัดการศพผู้เสียชีวิต", id: 1 },
  { title: "จำนวน", description: "320 ครอบครัว", id: 2 },
];
const places = [
  { title: "อำเภอ", description: "เมืองเลย", id: 1 },
  { title: "จำตำบล/แขวง", description: "เมือง", id: 2 },
  { title: "วันครบกำหนด ระยะเวลา", description: "45 วัน", id: 3 },
];
const pays = [
  { title: "จำนวนเงินขออนุมัติ", description: "223,740.00 บาท", id: 1 },
  {
    title: `จำนวนเงินทั้งหมด \"ตามจังหวัด\"`,
    description: "554,011.65 บาท",
    id: 2,
  },
  {
    title: `จำนวนเงินทั้งหมด \"ตามครั้งที่ขอ\"`,
    description: "1,671,623.00 บาท",
    id: 3,
  },
];
const allpay = {
  title: `จำนวนเงินทั้งหมด\"ตามที่ขอ\"`,
  description: "11,067,538.20 บาท",
};
definePageMeta({
  title: 'หน้าหลัก'
});
</script>

<style scoped>

</style>