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
const selecteddata = ref('SELECT INCOME PROOF')
const datas = ['I LIKE TO OPT-OUT NOMINEE', 'APRICAN']
</script>

<template>
  <VRow class="">
    <VCol
      cols="12"
      md="6"
    >
      <VCard>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">CHOOSE INCOME PROOF</label>
          </VCol>
          <VCol cols="12">
            <VCombobox
              v-model="selecteddata"
              :items="datas"
              placeholder="deployment"
            />
          </VCol>
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
