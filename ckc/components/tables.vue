<template>
  <UCard>
    <table class="min-w-full divide-y divide-gray-200 dark:divide-gray-700">
      <thead class="bg-green-500 text-white">
        <tr class="text-center">
          <th class="px-4 py-2"><UCheckbox v-model="valuecheck" /></th>
          <th class="px-4 py-2">ครั้งที่ขอ</th>
          <th class="px-4 py-2">ลำดับที่</th>
          <th class="px-4 py-2">ประเภทภัย</th>
          <th class="px-4 py-2">เลขหนังสือจังหวัด</th>
          <th class="px-4 py-2">เลข GFMIS</th>
          <th class="px-4 py-2">จังหวัด</th>
          <th class="px-4 py-2">ระยะเวลาคงเหลือ</th>
          <th class="px-4 py-2">สถานะ</th>
          <th class="px-4 py-2"></th>
        </tr>
      </thead>
      <tbody>
        <tr
          class="divide-x divide-gray-300 dark:divide-gray-800"
          v-for="user in users"
          :key="user.id"
        >
          <td class="px-4 py-2">
            <UCheckbox :v-model="user.check" />
          </td>
          <td class="px-4 py-2">
            <div class="rounded-xl bg-green-100 p-2 font-bold text-center">
              {{ user.requestNumber }}
            </div>
          </td>
          <td class="px-4 py-2">
            <div class="rounded-xl bg-green-100 p-2 font-bold text-center">
              {{ user.id }}
            </div>
          </td>
          <td class="px-4 py-2">{{ user.disasterType }}</td>
          <td class="px-4 py-2">{{ user.provinceBookNumber }}</td>
          <td class="px-4 py-2">{{ user.gfmisNumber }}</td>
          <td class="px-4 py-2">{{ user.province }}</td>
          <td class="px-4 py-2">{{ user.remainingTime }}</td>
          <td class="px-4 py-2">
            <UBadge :color="user.status ? 'green' : 'red'">
              {{ user.status ? "เปิดใช้งาน" : "ปิดใช้งาน" }}
            </UBadge>
          </td>
          <td class="px-4 py-2">
            <UButton size="xs" color="gray" icon="i-lucide-eye" />
          </td>
        </tr>
      </tbody>
    </table>
  </UCard>
</template>

<script setup>
import { ref, watch, computed } from 'vue'
const users = ref([
  {
    id: 1,
    requestNumber: "1",
    orderNumber: "A1",
    disasterType: "Flood",
    provinceBookNumber: "PB12345",
    gfmisNumber: "GF001",
    province: "Bangkok",
    remainingTime: "10 days",
    status: true,
    check: false
  },
  {
    id: 2,
    requestNumber: "1",
    orderNumber: "A2",
    disasterType: "Earthquake",
    provinceBookNumber: "PB12346",
    gfmisNumber: "GF002",
    province: "Chiang Mai",
    remainingTime: "5 days",
    status: false,
    check: false
  },
  {
    id: 3,
    requestNumber: "1",
    orderNumber: "A3",
    disasterType: "Storm",
    provinceBookNumber: "PB12347",
    gfmisNumber: "GF003",
    province: "Phuket",
    remainingTime: "15 days",
    status: true,
    check: false
  },
  {
    id: 4,
    requestNumber: "1",
    orderNumber: "A4",
    disasterType: "Fire",
    provinceBookNumber: "PB12348",
    gfmisNumber: "GF004",
    province: "Khon Kaen",
    remainingTime: "7 days",
    status: false,
    check: false
  },
  {
    id: 5,
    requestNumber: "1",
    orderNumber: "A5",
    disasterType: "Drought",
    provinceBookNumber: "PB12349",
    gfmisNumber: "GF005",
    province: "Udon Thani",
    remainingTime: "20 days",
    status: true,
    check: false
  },
]);
const valuecheck = computed({
  get() {
    return users.value.every(user => user.check)
  },
  set(val) {
    users.value.forEach(user => user.check = val)
  }
})


</script>

<style lang="scss" scoped>
</style>