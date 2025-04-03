<template>
  <UApp class="w-full">
    <div class="mt-5">
      <formdocument />
      <div class="flex justify-center items-center gap-3 mt-5">
        <btn-confirm />
        <btn-cancel />
      </div>
    </div>
  </UApp>
</template>

<script setup>
definePageMeta({
    title: "ส่งคืนเอกสาร"
})
</script>

<style lang="scss" scoped>
</style>