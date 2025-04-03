<template>
  <div>
    <div class="flex justify-start items-center gap-3 mb-2">
      <h1 class="font-bold text-sm md:text-xl">ส่งคืนเอกสาร</h1>
      <button
        :class="
          slc === 1
            ? 'bg-green-500  text-white font-bold py-2 px-4 rounded-xl'
            : 'text-gray-300 hover:bg-gray-200   font-bold py-2 px-4 rounded-xl'
        "
        @click="slc = 1"
      >
        คืนเรื่อง/ถอนเรื่องคืน
      </button>
      <button
        :class="
          slc === 2
            ? 'bg-green-500  text-white font-bold py-2 px-4 rounded-xl'
            : 'text-gray-300 hover:bg-gray-200   font-bold py-2 px-4 rounded-xl'
        "
        @click="slc = 2"
      >
        ปรับลด/ส่งคืนบางส่วน
      </button>
    </div>
    <div
      class="grid grid-cols-1 md:grid-cols-2 gap-x-10 gap-y-2 w-full max-w-3xl mx-auto"
    >
      <div v-for="data in datafield" class="flex flex-col" :key="data.id">
        <h1 class="text-black" v-if="data.id !== 5">{{ data.label }}</h1>
        <UInput
          v-if="data.id !== 5"
          v-model="data.value.value"
          :placeholder="data.placeholder"
          class="w-full "
          size="lg"
          :icon="data.id == 2 ? 'i-lucide-calendar bg-black' : ''"
          trailing
        />
        <h1 class="text-black" v-if="data.id == 5 && slc == 2">
          {{ data.label }}
        </h1>
        <UInput
          v-if="data.id == 5 && slc == 2"
          v-model="data.value.value"
          :placeholder="data.placeholder"
          class="w-full"
        />
      </div>
    </div>
   
  </div>
</template>

<script setup>
const slc = ref(1);
const username = ref("");
const datafield = [
  {
    label: "เลขที่หนังสือ",
    value: ref(""),
    placeholder: "กรอกเลขที่หนังสือ",
    id: 1,
  },
  {
    label: "วัน/เดือน/ปี",
    value: ref(""),
    placeholder: "กรอกวัน/เดือน/ปี",
    id: 2,
  },
  { label: "จำนวนเงิน", value: ref(""), placeholder: "กรอกจำนวนเงิน", id: 3 },
  { label: "สาเหตุ", value: ref(""), placeholder: "กรอกสาเหตุ", id: 4 },
  {
    label: "ระบุเงินส่งคืน",
    value: ref(""),
    placeholder: "ระบุจำนวนเงิน",
    id: 5,
  },
];
</script>

<style lang="scss" scoped>
</style>