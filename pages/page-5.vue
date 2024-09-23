<script lang="ts" setup>
const fname = ref('')
const mname = ref('')
const gender = ref('')
const dateofbirth = ref('')

const checkbox = ref(false)
const selectedItem = ref('MARRIED')
const items = ['MARRIED', 'SINGLE']
const selecteddata = ref('INDIAN')
const datas = ['INDIAN', 'APRICAN']
const show1 = ref(false)
const show2 = ref(true)
const password = ref('Password')
const confirmPassword = ref('wqfasds')

const rules = {
  required: (value: string) => !!value || 'Required.',
  min: (v: string) => v.length >= 8 || 'Min 8 characters',
}
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
            <label for="mname">NATIONALITY</label>
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
            <label for="mname">PERMANENT ADDRESS FROM DIGILOCKER</label>
          </VCol>
          <VCol cols="12"> <VTextarea placeholder="Placeholder Text" /></VCol>
        </VCol>
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="mname">CITY / AREA</label>
          </VCol>
          <VCol cols="12">
            <VTextField
              id="mname"
              v-model="mname"
              placeholder="dindigul"
              persistent-placeholder
            />
          </VCol>
        </VCol>
        <VRow class="px-4">
          <VCol
            cols="12"
            sm="6"
          >
            <label for="mname">STATE</label>
          </VCol>

          <VCol
            cols="12"
            sm="6"
          >
            <label for="mname">PINCODE</label>
          </VCol>
        </VRow>
        <VRow class="px-4">
          <VCol
            cols="12"
            sm="6"
          >
            <VTextField
              id="mname"
              v-model="mname"
              placeholder="TAMIL NADU"
              persistent-placeholder
            />
          </VCol>

          <VCol
            cols="12"
            sm="6"
          >
            <VTextField
              id="mname"
              v-model="mname"
              placeholder="613601"
              persistent-placeholder
            />
          </VCol>
        </VRow>
        <VCol
          cols="12"
          class="my-2"
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
              <VCol cols="10"
                ><VCardText
                  ><div class="text-[#8C57FF] font-bold text-xs mt-1">
                    COMMUNICATION SANE AS PERMANENT ADDRESS
                  </div></VCardText
                ></VCol
              >
            </VRow>
          </VCard>
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

