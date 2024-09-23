<script lang="ts" setup>
import file from '@images/file.png?raw'
const brokerage = [
  {
    title: 'Equity Intraday : 0.03%',
  },
  {
    title: 'Equity Delivery :0.30%',
  },
  {
    title: 'NSE & BSE Future :0.03%',
  },
  {
    title: 'Option :RS 50 per lot',
  },
  {
    title: 'MCX Future :0.02%',
  },
  {
    title: 'MCX Option :RS 50 per lot',
  },
  {
    title: 'Current Future and options RS 10 per lot',
  },
]
</script>

<template>
  <VRow class="">
    <VCol
      cols="12"
      md="6"
    >
      <VCard>
        <VImg
          :src="file"
          alt="Coming Soon"
          max-width="200"
          class="mx-auto"
        />
        <VCol class="d-flex justify-center text-gray text-xl font-bold">Traditional Brokerage</VCol>
        <VCol
          v-for="brokerages in brokerage"
          :key="brokerages"
          class="mx-4"
        >
          <VRow>
            <VCol
              cols="2"
              class="px-3"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="green"
                class="size-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="m4.5 12.75 6 6 9-13.5"
                />
              </svg>
            </VCol>
            <VCol cols="8"
              ><label>{{ brokerages.title }}</label></VCol
            >
          </VRow>
        </VCol>
        <VCol cols="12">
          <VBtn
            block
            type="submit"
          >
            NEXT STEP
          </VBtn>
        </VCol>

        <VCol cols="12">
          <VBtn
            block
            color="secondary"
            type="reset"
            variant="outlined"
          >
            Back to Previous
          </VBtn>
        </VCol>
      </VCard>
    </VCol>
  </VRow>
</template>
<style lang="scss">
.v-card-text {
  padding: 2px !important;
}
</style>
