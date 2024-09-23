<script lang="ts" >
export default {
  data() {
    return {
      emailAddress: '',
      isValidEmail: false,
      isError: false,
      isMobileNumberValid: false,
      mobileNumber: '',
      emailErrors: [],
    }
  },
  methods: {
    validateEmail() {
      const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/
      this.isValidEmail = emailRegex.test(this.emailAddress)
      this.emailErrors = []
      if (this.isValidEmail == false) {
        this.isError = true
        this.emailErrors.push('Enter Valid Email')
      } else {
        this.$router.push('/mainpage-2')
      }
    },
    validateMobileNumber() {
      const mobileNumberRegex = /^\(?([0-9]{3})\)?[-. ]?([0-9]{3})[-. ]?([0-9]{4})$/
      return mobileNumberRegex.test(this.mobileNumber)
    },
  },
}
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCard>
        <VRow>
          <VCol
            cols="12"
            md="6"
          >
            <IconBtn class="">
              <VIcon icon="ri-arrow-left-line" />
            </IconBtn>
          </VCol>
        </VRow>
        <VRow>
          <VCol
            cols="12"
            md="6"
            class="px-6"
          >
            <img
              src="@/public/envelop.jpeg"
              alt=""
              class="h-10 w-10" /></VCol
        ></VRow>
        <VRow>
          <VCol
            cols="12"
            md="6"
            class="px-6"
          >
            <VLabel class="font-bold text-sm">Add Email Address</VLabel>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. <br />Temporibus fugit alias dignissimos illo
              repellendus praesentium.
            </p>
          </VCol></VRow
        >
        <VRow class="pb-3 px-4">
          <VCol cols="12">
            <VTextField
              v-model="emailAddress"
              prepend-inner-icon="ri-mail-line"
              label="Email"
              type="email"
              :error-messages="emailErrors"
              placeholder="johndoe@example.com"
            /> </VCol
        ></VRow>

        <VCol
          cols="12"
          class="px-4"
        >
          <VBtn
            block
            color="primary"
            type="reset"
            @click="validateEmail"
          >
            verify Email Address
          </VBtn>
        </VCol></VCard
      ></VCol
    ></VRow
  >
</template>
<style lang="scss">
</style>
