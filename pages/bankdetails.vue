<script lang="ts" >
export default {
  data() {
    return {
      selectedaccounttypeButton: 'CURRENT',
    }
  },
  methods: {
    selectaccounttypeButton(option: string) {
      this.selectedaccounttypeButton = option
      console.log('Selected fund button value:', this.selectedaccounttypeButton)
    },
  },
}
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCard>
        <VCol class="px-3">Bank Details</VCol>
        <VCol class="font-bold text-lg pt-1">Link Your Bank Account</VCol>
        <VCol class="px-3 pt-1">From Which You Can Add and Withdraw Funds </VCol>
        <VCol class="py-1">
          <VLabel class="font-bold">Select Your Bank</VLabel>
        </VCol>
        <VCol class="py-1"
          ><VAutocomplete
            :items="items"
            placeholder="Select Option"
        /></VCol>
        <VCol>
          <VLabel class="font-bold">IFSC Code</VLabel>
        </VCol>
        <VCol class="py-1"> <VTextField /></VCol>

        <VCol>
          <VLabel class="font-bold">Account Type</VLabel>
        </VCol>
        <VRow class="px-3">
          <VCol>
            <button
              ref="fundButton1"
              class="gender-button"
              :class="{ selected: selectedaccounttypeButton === 'SAVINGS' }"
              @click="selectaccounttypeButton('SAVINGS')"
            >
              SAVINGS
            </button>
            <button
              ref="fundButton2"
              class="gender-button"
              :class="{ selected: selectedaccounttypeButton === 'CURRENT' }"
              @click="selectaccounttypeButton('CURRENT')"
            >
              CURRENT
            </button>
          </VCol></VRow
        >

        <VCol>
          <VLabel class="font-bold">Account Number</VLabel>
        </VCol>
        <VCol class="py-1"> <VTextField /></VCol>
        <VCol>
          <VLabel class="font-bold">Repeat Account Number</VLabel>
        </VCol>
        <VCol class="py-1"> <VTextField /></VCol>
        <VCol
          cols="12"
          class="pb-10"
        >
          <VBtn
            block
            type="submit"
            to="/selfie"
          >
            PROCEED
          </VBtn>
        </VCol></VCard
      ></VCol
    ></VRow
  >
</template>
<style lang="scss">
</style>
