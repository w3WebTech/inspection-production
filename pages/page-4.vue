<script lang="ts" setup>
const fname = ref('')
const mname = ref('')
const gender = ref('')
const dateofbirth = ref('')
const password = ref<string>()
const checkbox = ref(false)
const selectedItem = ref('MARRIED')
const items = ['MARRIED', 'SINGLE']
const selecteddata = ref('BE')
const datas = ['BE', 'BSC']
</script>

<template>
  <VRow class="">
    <VCol
      cols="12"
      md="6"
    >
      <VCard title="YOUR PERSONAL DETAILS">
        <VCol cols="12">
          <VCol
            cols="12"
            md="12"
            class="text-sm"
          >
            <label for="fname">FATHER'S NAME</label>
          </VCol>

          <VCol
            cols="12"
            md="12"
            class=""
          >
            <VTextField
              id="fname"
              v-model="fname"
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
            <label for="mname">MOTHER'S NAME</label>
          </VCol>

          <VCol
            cols="12"
            md="12"
            class=""
          >
            <VTextField
              id="mname"
              v-model="mname"
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
            <label for="mname">GENDER FROM DIGILOCKER</label>
          </VCol>

          <VCol
            cols="12"
            md="12"
            class=""
          >
            <VTextField
              id="gender"
              v-model="gender"
              placeholder="MALE"
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
            <label for="mname">MARRITAL STATUS</label>
          </VCol>
          <VCol cols="12">
            <VCombobox
              v-model="selectedItem"
              :items="items"
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
            <label for="mname">EDUCATION - QUALIFICATION</label>
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

