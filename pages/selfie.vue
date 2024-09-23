<script lang="ts" >
export default {
  data() {
    return {
      checkbox: false,
      checkbox1: false,
      checkbox2: false,
    }
  },
  methods: {},
}
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCard>
        <VCol class="px-3">Selfie</VCol>
        <VCol class="font-bold text-lg pt-1">Click A Selfie</VCol>
        <VCol class="px-3 py-1">Your Live Photo is required to sequirely open your demat account</VCol>
        <VCol>
          <img
            src="@/public/selfie.jpeg"
            alt=""
            class="w-full"
          />
        </VCol>
        <VCol>
          <VAlert
            border="start"
            border-color="warning"
          >
            To proceed with clicking a selfie,we need access to your webcam and location.Please allow the permissions to
            proceed.
          </VAlert></VCol
        >

        <VRow class="px-3 py-4 pb-15">
          <VCol cols="12">
            <VBtn
              block
              type="submit"
              to="/signatureupload"
            >
              OPEN CAMERA
            </VBtn>
          </VCol>
        </VRow>
      </VCard></VCol
    ></VRow
  >
</template>
<style lang="scss">
</style>
