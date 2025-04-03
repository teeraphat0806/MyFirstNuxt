<template>
  <div>
    <div class="flex justify-start items-center mb-10">
      <h1 class="font-bold text-sm md:text-xl">บันทึกข้อมูล/</h1>
      <h1 class="font-medium text-sm md:text-xl ">หลักการกรมบัญชีกลาง</h1>
    </div>
    <div
      class="grid grid-cols-1 md:grid-cols-2 gap-x-10 gap-y-2 w-full max-w-3xl mx-auto"
    >
      <div v-for="data in datafield" class="flex flex-col" :key="data.id">
        <div class="flex">
          <h1 class="text-black" v-if="data.id !== 5">{{ data.label }}</h1>
          <h1 class="text-red-500" v-if="data.id !== 5">{{ data.detail }}</h1>
        </div>
        <UInput
          v-if="data.id !== 5"
          v-model="data.value.value"
          :placeholder="data.placeholder"
          class="w-full"
          size="lg"
          :icon="data.id == 2 ? 'i-lucide-calendar bg-black' : ''"
          trailing
        />
        <div class="flex">
          <h1 class="text-black" v-if="data.id == 5 && slc == 2">
            {{ data.label }}
          </h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  datafield: {
    type: Array,
    required: true,
  },
});
</script>

<style lang="scss" scoped>
</style>