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
      if (this.isValidEmail == false) {
        this.isError = true
      } else {
        this.$router.push('/verification')
      }
    },
    validateMobileNumber(): any {
      const mobileNumberRegex = /^\(?([0-9]{3})\)?[-. ]?([0-9]{3})[-. ]?([0-9]{4})$/
      console.log(mobileNumberRegex.test(this.mobileNumber), 'valid')
      this.isMobileNumberValid = mobileNumberRegex.test(this.mobileNumber)
      if (this.isMobileNumberValid == true) {
        this.$router.push('/otp')
      } else {
        this.emailErrors.push('Enter valid Number')
      }
    },
  },
}
</script>

<template>
  <VRow class="d-flex justify-start">
    <VCol
      cols="12"
      md="6"
    >
      <VRow class="py-4">
        <VCol
          cols="3"
          md="4"
          class="px-6"
        >
          <img
            src="@images/phonepay.png"
            alt=""
            class="h-10 w-10"
        /></VCol>
        <VCol
          cols="1"
          md="2"
          class="px-6"
        >
          <IconBtn class="">
            <VIcon icon="ri-arrow-right-line" />
          </IconBtn>
        </VCol>
        <VCol
          cols="4"
          md="4"
          class="px-6"
        >
          <img
            src="@/public/download.png"
            alt=""
            class="h-10 w-10"
        /></VCol>
      </VRow>
      <VCol class="font-bold text-lg text-black px-4"
        >Use Your PhonePe Account to <br />
        proceed with Share Market</VCol
      >
      <VCol cols="12">
        <VCol
          cols="12"
          md="12"
          class="text-sm"
        >
          <label for="mobile">Enter Mobile Number</label>
        </VCol>

        <VCol
          cols="12"
          md="12"
          class="pb-0"
        >
          <VTextField
            id="mobile"
            v-model="mobileNumber"
            type="number"
            placeholder="+91 1234567890"
            :error-messages="emailErrors"
            persistent-placeholder
          />
        </VCol>
      </VCol>
      <VCol
        cols="12"
        class="px-5"
      >
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Nisi est, dolorum inventore voluptatem animi, sed
        itaque quibusdam enim assumenda tenetur soluta.</VCol
      >
      <VCol
        cols="12"
        class="px-4"
      >
        <VBtn
          block
          color="primary"
          type="reset"
          @click="validateMobileNumber"
        >
          Proceed
        </VBtn>
      </VCol>
    </VCol></VRow
  >
</template>
<style lang="scss">
</style>
