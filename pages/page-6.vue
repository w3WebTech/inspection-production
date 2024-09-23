<script lang="ts" setup>
const fname = ref('')
const mname = ref('')
const gender = ref('')
const dateofbirth = ref('')
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
      <VCard title="YOUR ADDRESS DETAILS">
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">NOMINEE DETAILS</label>
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
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">TRADING EXPERIANCE</label>
          </VCol>
          <VCol cols="12">
            <VCombobox
              v-model="selectedexperiance"
              :items="experiances"
              placeholder="deployment"
            />
          </VCol>
        </VCol>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">SELECT ANNUAL INCOME</label>
          </VCol>
          <VCol cols="12">
            <VCombobox
              v-model="selectedincome"
              :items="income"
              placeholder="deployment"
            />
          </VCol>
        </VCol>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">SELECT OCCUPATION</label>
          </VCol>
          <VCol cols="12">
            <VCombobox
              v-model="selectedoccupation"
              :items="occupation"
              placeholder="deployment"
            />
          </VCol>
        </VCol>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">ARE YOY PEP/RELATED TO PEP (PEP= POLITICALLY EXPOSED PERSON) </label>
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
                    <label for=""> NO ,I AM NOT</label></VCol
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
                    <label for="">YES , I AM</label></VCol
                  >
                </VRow>
              </VCardText>
            </VCard>
          </VCol>
        </VRow>
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
