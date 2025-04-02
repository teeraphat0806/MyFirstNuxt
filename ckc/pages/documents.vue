<template>
  <UApp class="w-full">
    <!-- Section: Header and Step Icons -->
    <div class="flex flex-col items-center gap-4 ">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-4 ">
        <UCard class="md:w-full lg:w-100">
          <div class="space-y-2 ">
            <headtext
              title="เอกสารร่าง 1 "
              icon="i-mdi-database"
              custom="rounded-full bg-gray-200"
            />
            <span class="m-2" />
            <div v-for="data in datas" :key="data.id" >
              <itemlist :title="data.title" :description="data.description" />
            </div>
          </div>
        </UCard>
        <UCard class="w-full lg:w-100">
          <div class="space-y-2">
            <headtext
              title="เอกสารร่าง 2 "
              icon="i-mdi-database"
              custom="rounded-full bg-gray-200"
            /><span class="m-2" />
            <div v-for="data in datas" :key="data.id">
              <itemlist :title="data.title" :description="data.description" />
            </div>
          </div>
        </UCard>
        <UCard class="md:w-full lg:w-100">
          <div class="space-y-2">
           
              <headtext
                title="เอกสารร่าง 3 "
                icon="i-mdi-database"
                custom="rounded-full bg-gray-200"
              />
            <span class="m-2" />
            <div v-for="data in datas" :key="data.id">
              <itemlist :title="data.title" :description="data.description" />
            </div>
          </div>
        </UCard>
        <UCard class="md:w-full lg:w-100">
          <div class="space-y-2">
            <headtext
              title="เอกสารร่าง 4 "
              icon="i-mdi-database"
              custom="rounded-full bg-gray-200"
            /><span class="m-2" />
            <div v-for="data in datas" :key="data.id">
              <itemlist :title="data.title" :description="data.description" />
            </div>
          </div>
        </UCard>
      </div>
    </div>
  </UApp>
</template>

<script setup>
definePageMeta({
  title: "เอกสารร่าง",
});
const datas = [
  { title: "ปีงบประมาณ", description: "2567", id: 1 },
  { title: "จังหวัด", description: "เลย", id: 2 },
  { title: "ด้าน", description: "ด้านการดำรงชีพ", id: 3 },
  { title: "ประเภทภัย", description: "อุทกภัย", id: 4 },
];
</script>

<style lang="scss" scoped>
</style>