<script lang="ts" setup>
const firstName = ref('')
const lastName = ref('')
const city = ref('')
const country = ref('')
const company = ref('')
const email = ref('')
const checkbox = ref(false)

const cardData = [
  {
    subtitle: 'NSE CASH',
  },
  {
    subtitle: 'BSE CASE',
  },
  {
    subtitle: 'NSE F & O',
  },
  {
    subtitle: 'NSE COMMODITY',
  },
  {
    subtitle: 'BSE F & O',
  },
  {
    subtitle: 'BSE COMMODITY',
  },
  {
    subtitle: 'NSE CD',
  },
  {
    subtitle: 'BSE CD',
  },
  {
    subtitle: 'MCE',
  },
  {
    subtitle: 'MSE CD',
  },
]
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCard title="Trading Segments">
        <VForm
          @submit.prevent="() => {}"
          class="p-4"
        >
          <VRow>
            <VCol
              cols="12"
              md="6"
              v-for="data in cardData"
              :key="data"
            >
              <VCard class="">
                <VRow>
                  <VCol cols="2"
                    ><VCardText>
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="#8C57FF"
                        class="size-6"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z"
                        />
                      </svg> </VCardText
                  ></VCol>
                  <VCol cols="7"
                    ><VCardText
                      ><div class="text-[#8C57FF] font-bold text-xs mt-1">{{ data.subtitle }}</div></VCardText
                    ></VCol
                  >
                  <VCol cols="1"
                    ><VCardText
                      ><svg
                        xmlns="http://www.w3.org/2000/svg"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="#8C57FF"
                        class="size-6"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M16.5 6v.75m0 3v.75m0 3v.75m0 3V18m-9-5.25h5.25M7.5 15h3M3.375 5.25c-.621 0-1.125.504-1.125 1.125v3.026a2.999 2.999 0 0 1 0 5.198v3.026c0 .621.504 1.125 1.125 1.125h17.25c.621 0 1.125-.504 1.125-1.125v-3.026a2.999 2.999 0 0 1 0-5.198V6.375c0-.621-.504-1.125-1.125-1.125H3.375Z"
                        />
                      </svg> </VCardText
                  ></VCol>
                </VRow>
              </VCard>
            </VCol>
          </VRow>
        </VForm>
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
  padding-left: 4px !important;
  padding-right: 4px !important;
}
</style>

