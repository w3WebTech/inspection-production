<script lang="ts" setup>
const pannumber = ref('')
const adhar = ref('')
const referalcode = ref('')
const dateofbirth = ref('')
const password = ref<string>()
const checkbox = ref(false)
</script>

<template>
  <VRow class="">
    <VCol
      cols="12"
      md="6"
    >
      <VCard title="PAN DETAILS">
        <VForm @submit.prevent="() => {}">
          <VRow class="px-5">
            <!-- 👉 First Name -->
            <VCol
              cols="12"
              md="12"
              class="p-[2px]"
            >
              <VRow class="px-4">
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
                    class="text-sm py-5 px-3 my-1 d-flex justify-center items-center text-center"
                    rounded="none"
                  >
                    verify
                  </VBtn>
                </VCol>
              </VRow>
            </VCol>
            <!-- <VCol
              cols="12"
              md="6"
              class="text-sm"
            >
              <label for="pannumber">PAN NUMBER</label>
            </VCol>

            <VCol
              cols="12"
              md="6"
              class=""
            >
              <VTextField
                id="pannumber"
                v-model="pannumber"
                placeholder="abc 1234 2332 43243"
                persistent-placeholder
              />
              <VTextField
                id="pannumber"
                v-model="pannumber"
                placeholder="abc 1234 2332 43243"
                persistent-placeholder
              />
            </VCol> -->

            <VCol cols="12">
              <VCol
                cols="12"
                md="12"
                class="text-sm"
              >
                <label for="dateofbirth">DATE OF BIRTH</label>
              </VCol>

              <VCol
                cols="12"
                md="12"
                class=""
              >
                <VTextField
                  id="dateofbirth"
                  v-model="dateofbirth"
                  placeholder="DD - MM - YYYY"
                  persistent-placeholder
                />
              </VCol>
            </VCol>
            <VCol cols="12">
              <!-- 👉 First Name -->
              <VCol
                cols="12"
                md="12"
                class="text-sm"
              >
                <label for="adhar">AADHAAR NUMBER (LAST 4 DIGIT)</label>
              </VCol>

              <VCol
                cols="12"
                md="12"
                class=""
              >
                <VTextField
                  id="adhar"
                  v-model="adhar"
                  placeholder="1234 5678 1234"
                  persistent-placeholder
                />
              </VCol>
            </VCol>
          </VRow>
        </VForm>
        <VRow class="my-1 px-6">
          <VCol
            cols="12"
            md="6"
          >
            <VBtn
              block
              type="submit"
              class="text-sm"
            >
              FAST MODE <br />(via digilocker otp)
            </VBtn>
          </VCol>
          <VCol
            cols="12"
            md="6"
          >
            <VBtn
              block
              type="submit"
              class="text-sm"
            >
              NEXT STEP <br />(via proof upload)
            </VBtn>
          </VCol>
        </VRow>
        <VRow class="my-1 px-6">
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
        </VRow>
      </VCard>
    </VCol>
  </VRow>
</template>
<style lang="scss">
.v-col .v-col-12 {
  padding: 6px !important;
  padding-top: 3px !important;
  padding-bottom: 3px !important;
}
.v-col-1 {
  padding-left: 0 !important;
  padding-right: 0 !important;
  padding-top: 13px !important;
  margin: 0 !important;
}
.v-col-9 {
  padding-left: 0 !important;
  padding-right: 0 !important;

  margin: 0 !important;
}
</style>
