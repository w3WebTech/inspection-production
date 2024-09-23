<script lang="ts" setup>
const toggleCheckbox1 = ref(false)
const toggleCheckbox2 = ref(false)
const toggleCheckbox3 = ref(false)
const toggleCheckbox4 = ref(false)
const toggleCheckbox5 = ref(false)
const toggleCheckbox6 = ref(false)
const isDialogVisible = ref(true)
const skill = ref(60)
</script>

<template>
  <VLabel class="font-bold px-3"> Final routing page </VLabel>
  <VCol
    class="fixed bottom-0 bg-white h-[100px] layout-page-content"
    cols="12"
    md="6"
  >
    <div class="demo-space-y px-4">
      <div class="flex justify-end">{{ Math.ceil(skill) }}%</div>
      <VProgressLinear
        v-model="skill"
        color="primary"
        height="20"
      >
      </VProgressLinear>
    </div>
  </VCol>
</template>
<style lang="scss">
.layout-page-content {
}
.layout-page-content1 {
  padding-inline: 1.5rem !important;
}
</style>
