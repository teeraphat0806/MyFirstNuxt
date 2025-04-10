<template>
  <UApp>
    <div>
      <UCard class="bg-[#F9F9F9] mb-4 sticky top-0 z-50 overflow-hidden">
        <div class="space-y-5 md:space-y-0 md:grid md:grid-cols-5 gap-4">
          <UFormField :error="errors.fiscalYear" required>
            <template #label>
              <span class="text-xl text-black">ปีงบประมาณ</span>
            </template>
            <USelect
              v-model="formState.fiscalYear"
              class="w-full"
              :items="years.map((y) => ({ ...y, value: String(y.value) }))"
              placeholder="กรุณาเลือก"
            />
          </UFormField>
          <UFormField :error="errors.fiscalYear" required>
            <template #label>
              <span class="text-xl text-black">ด้าน</span>
            </template>
            <USelect
              v-model="formState.fiscalYear"
              class="w-full"
              :items="years.map((y) => ({ ...y, value: String(y.value) }))"
              placeholder="กรุณาเลือก"
            />
          </UFormField>
          <UFormField :error="errors.fiscalYear" required>
            <template #label>
              <span class="text-xl text-black">จังหวัด</span>
            </template>
            <USelect
              v-model="formState.fiscalYear"
              class="w-full"
              :items="years.map((y) => ({ ...y, value: String(y.value) }))"
              placeholder="กรุณาเลือก"
            />
          </UFormField>
          <UFormField :error="errors.fiscalYear" required>
            <template #label>
              <span class="text-xl text-black">ประเภทภัย</span>
            </template>
            <USelect
              v-model="formState.fiscalYear"
              class="w-full"
              :items="years.map((y) => ({ ...y, value: String(y.value) }))"
              placeholder="กรุณาเลือก"
            />
          </UFormField>
          <div class="flex items-end">
            <UCheckbox
              v-model="other"
              label="อื่นๆ"
              @change="clearDangerTypeOther"
            />
            <Transition name="fade">
              <UInput
                class="ms-2 w-full"
                :ui="{
                  base: 'ring-0 bg-transparent border-b border-(--ui-primary) rounded-b-none focus:inset-ring-0 focus-visible:ring-0 px-0 mx-2',
                }"
              />
            </Transition>
          </div>
        </div>
        <div class="flex gap-3">
          <UButton
            class="mt-5 flex-1 w-full justify-center flex disabled:opacity-50 text-xl"
          >
            สร้าง
          </UButton>
          <UButton
            class="mt-5 w-[150px] justify-center flex disabled:opacity-50 text-xl bg-blue-400"
          >
            บันทึกร่าง
          </UButton>
          <UButton
            color="error"
            class="mt-5 w-[150px] justify-center flex disabled:opacity-50 text-xl"
          >
            ยกเลิก
          </UButton>
        </div>
      </UCard>
      <UCard class="bg-[#F9F9F9] mb-4 sticky top-0 z-50 overflow-hidden">
        <div class="">
          <p class="text-2xl font-bold">ข้อมูลหนังสือ</p>
          <hr class="border-2 border-black" />
          <div class="mt-5 space-y-5 md:space-y-0 md:grid md:grid-cols-4 gap-4">
            <div v-for="(item, index) in items" :key="index">
              <UFormField :error="errors.fiscalYear" required>
                <template #label>
                  <span class="text-[1rem] text-black">{{ item.label }}</span>
                </template>
                <UFormField :error="item.error">
                  <UInput placeholder="กรอกข้อมูล" class="w-full" />
                </UFormField>
              </UFormField>
            </div>
            <UFormField
              label="วันที่ประกาศภัย (45วัน)"
              name="announceDate"
              class="w-full"
              required
            >
              <DatePicker
                v-model="formState.announceDate"
                :max-date="new Date()"
                placeholder="เลือกวันที่"
                class="w-full"
              />
            </UFormField>
          </div>
          <div class="mt-5 space-y-5 md:space-y-0 md:grid md:grid-cols-5 gap-4">
            <UFormField required>
              <template #label>
                <span class="text-[1rem] text-black">เลขหนังสือจังหวัด</span>
              </template>
              <UFormField error="ห้ามเว้นว่างเลขที่หนังสือจังหวัด">
                <UInput placeholder="กรอกข้อมูล" class="w-full" />
              </UFormField>
            </UFormField>

            <UFormField name="announceDate" class="w-full" required>
              <template #label>
                <span class="text-[1rem] text-black">วันที่ผ่านการลงรับ</span>
                <span
                  class="hidden group-hover:block text-[1rem] text-black bg-white p-1 rounded shadow-md"
                  style="top: 100%; left: 0"
                >
                  เอกสารGFMIS (75วัน)
                </span>
              </template>
              <DatePicker
                v-model="formState.announceDate"
                :max-date="new Date()"
                placeholder="เลือกวันที่"
                class="w-full"
              />
            </UFormField>
            <UFormField :error="errors.fiscalYear" required>
              <template #label>
                <span class="text-[1rem] text-black">วงเงิน</span>
              </template>
              <USelect
                v-model="formState.fiscalYear"
                class="w-full"
                :items="years.map((y) => ({ ...y, value: String(y.value) }))"
                placeholder="กรุณาเลือก"
              />
            </UFormField>
            <UFormField :error="errors.fiscalYear" required>
              <template #label>
                <span class="text-[1rem] text-black">ปี GFMIS</span>
              </template>
              <USelect
                v-model="formState.fiscalYear"
                class="w-full"
                :items="years.map((y) => ({ ...y, value: String(y.value) }))"
                placeholder="กรุณาเลือก"
              />
            </UFormField>
            <UFormField required>
              <template #label>
                <span class="text-[0.9rem] text-black">เลขที่เอกสารGFMIS</span>
              </template>
              <UFormField>
                <UInput placeholder="ระบุตัวเลข GFMIS" class="w-full" />
              </UFormField>
            </UFormField>
          </div>
          <div class="gap-4 mt-4">
            <UFormField label="ชั้นความเร็ว">
              <URadioGroup
                v-model="formState.urgentLevel"
                orientation="horizontal"
                default-value="NORMAL"
                :items="urgent"
              />
              <p class="text-[#FFB800] mt-2">
                *หมายเหตุ : ถ้าไม่ระบุชั้นของความเร็วเอกสาร คือ เอกสารปกติ
              </p>
            </UFormField>
          </div>
          <div class="">
            <p class="text-2xl font-bold mt-5">ข้อมูลภัย</p>
            <hr class="border-2 border-black" />
            <div
              class="mt-5 space-y-5 md:space-y-0 md:grid md:grid-cols-4 gap-4"
            >
              <UFormField name="announceDate" class="w-full">
                <template #label>
                  <span class="text-[1rem] text-black">ห้วงเกิดภัย</span>
                </template>
                <DatePicker
                  v-model="formState.announceDate"
                  :max-date="new Date()"
                  placeholder="เลือกวันที่"
                  class="w-full"
                />
              </UFormField>
              <UFormField name="announceDate" class="w-full">
                <template #label>
                  <span class="text-[1rem] text-black">ขอขยายเวลาถึง</span>
                </template>
                <DatePicker
                  v-model="formState.announceDate"
                  :max-date="new Date()"
                  placeholder="เลือกวันที่"
                  class="w-full"
                />
              </UFormField>
            </div>
          </div>
          <div class="">
            <p class="text-2xl font-bold mt-5">สถานที่ดำเนินการ</p>
            <hr class="border-2 border-black" />
            <div
              class="mt-5 space-y-5 md:space-y-0 md:grid md:grid-cols-4 gap-4"
            ></div>
          </div>
          <div class="">
            <p class="text-2xl font-bold mt-5">รายการช่วยเหลือ</p>
            <hr class="border-2 border-black" />
            <div
              class="mt-5 space-y-5 md:space-y-0"
            >
              <UFormField required>
              <template #label>
                <span class="text-[0.9rem] text-black">หลักเกณฑ์</span>
              </template>
              <UFormField>
                 <USelect
              v-model="formState.fiscalYear"
              class="w-full"
              :items="years.map((y) => ({ ...y, value: String(y.value) }))"
              placeholder="กรุณาเลือก"
            />
              </UFormField>
            </UFormField>
            </div>
          </div>
          <div class="">
            <p class="text-2xl font-bold mt-5">ค่าใช้จ่าย</p>
            <hr class="border-2 border-black" />
            <div
              class="mt-5 space-y-5 md:space-y-0 md:grid md:grid-cols-4 gap-4"
            >
            <div v-for="(item, index) in items2" :key="index">
              <UFormField v-if="index==0" :error="errors.fiscalYear" required>
                <template #label>
                  <div class="group relative">
                  <span class="text-[1rem] text-black">{{ item.label }}</span>
                  <span class="mt-1">   </span>
                  </div>
                </template>
                <UFormField :error="item.error">
                  <UInput placeholder="กรอกข้อมูล" class="w-full" />
                </UFormField>
              </UFormField> 
              <UFormField v-if="index!=0" :error="errors.fiscalYear" required>
                <template #label>
                  <span class="text-[1rem] text-black">{{ item.label }}</span>
                </template>
                <UFormField :error="item.error">
                  <UInput placeholder="กรอกข้อมูล" class="w-full" />
                </UFormField>
              </UFormField> 

            </div>

            </div>
          </div>
        </div>
      </UCard>
    </div>
  </UApp>
</template>

<script setup>
import { reactive } from "vue";
import DatePicker from "@vuepic/vue-datepicker";
import "@vuepic/vue-datepicker/dist/main.css";

// กำหนดข้อมูลปีงบประมาณ
const years = [
  { label: "2565", value: 2565 },
  { label: "2566", value: 2566 },
  { label: "2567", value: 2567 },
];

// ข้อมูลตัวเลือกสำหรับชั้นความเร็ว
const urgent = [
  { label: "ด่วน", value: "URGENT" },
  { label: "ด่วนมาก", value: "VERY_URGENT" },
  { label: "ด่วนที่สุด", value: "MOST_URGENT" },
];

// สถานะของฟอร์ม
const formState = reactive({
  fiscalYear: null,
  announceDate: null,
  urgentLevel: "NORMAL", // ค่าเริ่มต้นของชั้นความเร็ว
});

// ตัวอย่างการจัดการข้อผิดพลาด
const errors = reactive({
  fiscalYear: null, // ข้อผิดพลาดสำหรับปีงบประมาณ
});
const items = [
  { label: "เลขที่รับ บห.ตส", error: "ห้ามเว้นว่างเลขที่รับ บห.ตส" },
  { label: "เลขที่รับ ชภ.", error: "ห้ามเว้นว่างเลขที่รับ ชภ." },
  { label: "เลขที่รับ สล.", error: "ห้ามเว้นว่างเลขที่รับ สล." },
];
const items2 = [
  { label: "จำนวนเงินขออนุมัติ ", error: "กรุณากรอกข้อมูล" },
  { label: "จำนวนเงินทั้งหมด ตามจังหวัด", error: "กรุณากรอกข้อมูล" },
  { label: "จำนวนเงินทั้งหมด ตามครั้งที่ขอ", error: "กรุณากรอกข้อมูล" },
  { label: "จำนวนเงินทั้งหมด ตามที่ขอ", error: "กรุณากรอกข้อมูล" },
];
definePageMeta({
  title: "ระบบตรวจติดตาม",
});
</script>

<style lang="scss" scoped>
/* เพิ่มสไตล์ที่นี่หากจำเป็น */
</style>