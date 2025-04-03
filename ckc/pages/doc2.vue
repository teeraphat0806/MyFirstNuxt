<template>
  <UApp class="w-full">
    <div class="rounded-lg bg-gray-200 p-5">
      <formpopup :datafield="datafield" />
      <div class="flex justify-center items-center gap-3 mt-5">
        <btn-confirm />
        <btn-cancel />
      </div>
    </div>
  </UApp>
</template>

<script setup>
definePageMeta({
  title: "บันทึกข้อมูล/หลักการกรมบัญชีกลาง"
});

const datafield = [
  {
    label: "หลักการกรมบัญชีกลาง",
    value: ref(""),
    placeholder: "กรุณาพิมพ์ข้อมูล",
    detail: "",
    id: 1,
  },
  {
    label: "วัน/เดือน/ปี",
    value: ref(""),
    placeholder: "กรุณาเลือกวันเดือนปี",
    detail: "",
    id: 2,
  },
  { label: "วงเงินที่ขออนุมัติ", value: ref(""), placeholder: "กรอกจำนวนเงิน", detail: "", id: 3 },
  { label: "กรุณาพิมพ์ข้อมูล", value: ref(""), placeholder: "กรอกสาเหตุ", detail: "", id: 4 },
  {
    label: "วงเงินอนุมัติ",
    value: ref(""),
    placeholder: "กรุณาพิมพ์ข้อมูล",
    detail: "",
    id: 6,
  },
  {
    label: `วงเงิน`,
    value: ref(""),
    placeholder: "วงเงินจะขึ้น Auto",
    detail: `"ไม่อนุมัติ"`,
    id: 7,
  },
  {
    label: `รายการ`,
    value: ref(""),
    placeholder: "กรุณาพิมพ์ข้อมูล",
    detail: `"ไม่อนุมัติ"`,
    id: 8,
  },
];
</script>

<style lang="scss" scoped>
</style>