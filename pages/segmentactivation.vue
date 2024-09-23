<script lang="ts" >
export default {
  data() {
    return {
      checkbox: false,
      checkbox1: false,
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
        <VCol class="font-bold text-lg">Select Segment For Activation</VCol>
        <VCol class="px-3 py-1">Select which market you want to trade in.This can be done later as well.</VCol>
        <VCol
          ><div class="border border-gray rounded-md">
            <VCol class="py-1">
              <VRow>
                <VCol
                  class="font-bold text-lg"
                  cols="10"
                  >Equities
                </VCol>
                <VCol cols="2"><VCheckbox v-model="this.checkbox" /></VCol>
              </VRow>
            </VCol>

            <VCol class="px-3 py-1">You can invest and trade in stocks and ETF's by activating this..</VCol>
          </div></VCol
        >
        <VCol
          ><div class="border border-gray rounded-md">
            <VCol class="py-1">
              <VRow>
                <VCol
                  class="font-bold text-lg"
                  cols="10"
                  >Futures & Options
                </VCol>
                <VCol cols="2"><VCheckbox v-model="this.checkbox1" /></VCol>
              </VRow>
            </VCol>

            <VCol class="px-3 py-1">Only select this if you're an experienced trader</VCol>
            <div class="bg-[#FFE8E8] text-[#FF8F35] px-3">hello</div>
          </div>
        </VCol>
        <VRow class="px-3 py-4">
          <VCol
            cols="12 "
            class="pt-10"
          >
            <VBtn
              block
              type="submit"
              to="/esign"
            >
              PROCEED
            </VBtn>
          </VCol>
        </VRow>
      </VCard></VCol
    ></VRow
  >
</template>
<style lang="scss">
</style>
