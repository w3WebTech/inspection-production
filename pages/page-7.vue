<script lang="ts" setup>
const fname = ref('')
const mname = ref('')
const micr = ref('')
const ac = ref('')
const checkbox = ref(false)
const checkbox1 = ref(false)
const selecteddata = ref('I LIKE TO OPT-OUT NOMINEE')
const datas = ['I LIKE TO OPT-OUT NOMINEE', 'APRICAN']
const selectedexperiance = ref('SELECT TRADING EXPERIANCE')
const experiances = ['I LIKE TO OPT-OUT NOMINEE', 'APRICAN']
const selectedoccupation = ref('SELECT OCCUPATION')
const occupation = ['I LIKE TO OPT-OUT NOMINEE', 'APRICAN']
const selectedincome = ref('SELECT ANNUAL INCOME')
const income = ['I LIKE TO OPT-OUT NOMINEE', 'APRICAN']
</script>

<template>
  <VRow class="">
    <VCol
      cols="12"
      md="6"
    >
      <VCard title="Bank Details">
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">BANK ACCOUNT TYPE </label>
          </VCol>
        </VCol>
        <VRow class="px-4">
          <VCol
            cols="12"
            md="6"
            class=""
          >
            <VCard>
              <VCardText class="">
                <VRow>
                  <VCol
                    cols="2"
                    class="px-5"
                  >
                    <VCheckbox v-model="checkbox" />
                  </VCol>
                  <VCol
                    cols="10"
                    class="my-2"
                  >
                    <label for="">SAVINGS</label></VCol
                  >
                </VRow>
              </VCardText>
            </VCard>
          </VCol>
          <VCol
            cols="12"
            md="6"
            class=""
          >
            <VCard>
              <VCardText class="">
                <VRow>
                  <VCol
                    cols="2"
                    class="px-5"
                  >
                    <VCheckbox v-model="checkbox1" />
                  </VCol>
                  <VCol
                    cols="10"
                    class="my-2"
                  >
                    <label for="">CURRENT</label></VCol
                  >
                </VRow>
              </VCardText>
            </VCard>
          </VCol>
        </VRow>
        <VCol
          cols="12"
          md="12"
          class="text-sm mt-2"
        >
          <label for="mname">IFSC CODE (Find my ifsc code)</label>
        </VCol>
        <VCol
          cols="12"
          md="12"
        >
          <VRow class="px-3">
            <VCol
              sm="11"
              cols="9"
            >
              <VTextField
                label="Include files"
                placeholder="Placeholder Text"
              />
            </VCol>
            <VCol
              sm="1"
              cols="1"
              class=""
            >
              <VBtn
                type="submit"
                class="text-sm py-5 my-1 d-flex justify-center text-center items-center"
                rounded="none"
              >
                GO
              </VBtn>
            </VCol>
          </VRow>
        </VCol>

        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="micr">MICR CODE (Find my micr code)</label>
          </VCol>

          <VCol
            cols="12"
            md="12"
            class=""
          >
            <VTextField
              id="micr"
              v-model="micr"
              persistent-placeholder
            />
          </VCol>
        </VCol>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">BANK NAME & FULL ADDRESS</label>
          </VCol>
          <VCol cols="12"> <VTextarea placeholder="Placeholder Text" /></VCol>
        </VCol>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="ac">ACCOUNT NUMBER</label>
          </VCol>

          <VCol
            cols="12"
            md="12"
            class=""
          >
            <VTextField
              id="ac"
              v-model="ac"
              persistent-placeholder
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
