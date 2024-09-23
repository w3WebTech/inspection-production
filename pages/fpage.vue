<template>
  <div>
    <VRow class="">
      <VCol
        cols="12"
        md="6"
      >
        <!-- 👉 Horizontal Form -->
        <VCard title="Let's Create your account in 10 min's">
          <VCardText class="px-5">
            <DemoFormLayoutHorizontalForm />
          </VCardText>
        </VCard>
      </VCol>
    </VRow>
  </div>
</template>
<script setup lang="ts">
import DemoFormLayoutHorizontalForm from '@/views/pages/form-layouts/DemoFormLayoutHorizontalForm.vue'
</script>
<style lang="scss">
.v-col .v-col-12 .v-col-md-9 {
  padding-top: 2px !important;
  padding: 0 !important;
}
</style>
