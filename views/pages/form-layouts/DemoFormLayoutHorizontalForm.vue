<script lang="ts" setup>
const firstName = ref('')
const email = ref('')
const referalcode = ref('')
const mobile = ref<number>()
const password = ref<string>()
const checkbox = ref(false)
</script>

<template>
  <VForm @submit.prevent="() => {}">
    <VRow>
      <VCol cols="12">
        <!-- 👉 First Name -->
        <VCol
          cols="12"
          md="12"
          class="text-sm"
        >
          <label for="firstName">NAME AS PER PAN</label>
        </VCol>

        <VCol
          cols="12"
          md="12"
          class=""
        >
          <VTextField
            id="firstName"
            v-model="firstName"
            placeholder="John"
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
          <label for="mobile">MOBILE NO</label>
        </VCol>

        <VCol
          cols="12"
          md="12"
          class=""
        >
          <VTextField
            id="mobile"
            v-model="mobile"
            type="number"
            placeholder="+1 123 456 7890"
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
          <label for="email">EMAIL ID</label>
        </VCol>

        <VCol
          cols="12"
          md="12"
          class=""
        >
          <VTextField
            id="email"
            v-model="email"
            placeholder="John@gmail.com"
            persistent-placeholder
          />
        </VCol>
      </VCol>
      <VCol
        offset-md="3"
        cols="12"
        md="9"
      >
        <div class="d-flex justify-end text-sm text-primary px-2">change Mail</div>
      </VCol>
      <VCol cols="12">
        <!-- 👉 First Name -->
        <VCol
          cols="12"
          md="12"
          class="text-sm"
        >
          <label for="referalcode">REFFERAL CODE</label>
        </VCol>

        <VCol
          cols="12"
          md="12"
          class=""
        >
          <VTextField
            id="referalcode"
            v-model="referalcode"
            placeholder="12354"
            persistent-placeholder
          />
        </VCol>
      </VCol>

      <!-- 👉 Remember me -->
      <VCol cols="12">
        <VRow
          no-gutters
          class="px-2"
        >
          <VCol cols="2">
            <VTextField
              placeholder="0"
              maxlength="1"
              persistent-placeholder
            />
          </VCol>
          <VCol cols="2">
            <VTextField
              placeholder="0"
              maxlength="1"
              persistent-placeholder
            />
          </VCol>
          <VCol cols="2">
            <VTextField
              placeholder="0"
              maxlength="1"
              persistent-placeholder
            />
          </VCol>
          <VCol cols="2">
            <VTextField
              placeholder="0"
              maxlength="1"
              persistent-placeholder
            />
          </VCol>
          <VCol cols="2">
            <VTextField
              placeholder="0"
              maxlength="1"
              persistent-placeholder
            /> </VCol
          ><VCol cols="2">
            <VTextField
              placeholder="0"
              maxlength="1"
              persistent-placeholder
            />
          </VCol>
        </VRow>
      </VCol>
      <VCol
        offset-md="3"
        cols="12"
        md="9"
      >
        <div class="d-flex justify-end text-sm text-primary px-2">resend OTP</div>
      </VCol>
      <VCol
        cols="12"
        class="pb-6"
      >
        <VBtn
          block
          type="submit"
        >
          GET OTP
        </VBtn>
      </VCol>
    </VRow>
  </VForm>
</template>
<style lang="scss">
.v-col .v-col-12 {
  padding: 6px !important;
  padding-top: 3px !important;
  padding-bottom: 3px !important;
}
</style>
