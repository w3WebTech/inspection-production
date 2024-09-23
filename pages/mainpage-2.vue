<script lang="ts" >
export default {
  data() {
    return {
      emailAddress: '',
      isValidEmail: false,
      isError: false,
      isMobileNumberValid: false,
      mobileNumber: '',

      solidCardData: [
        {
          cardBg: '#8C57FF',
          title: 'Facebook Card',
          icon: 'ri-facebook-circle-line',
          text: "You've read about the importance of being courageous, rebellious and imaginative. These are all vital ingredients.",

          avatarName: 'Eugene Clarke',
          likes: '3.2k',
          share: '49',
        },
      ],
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
      }
    },
  },
}
</script>

<template>
  <VRow class="px-3">
    <VCol
      cols="12"
      md="6"
      class="d-flex justify-start"
    >
      <img
        src="@/public/plant.jpeg"
        alt=""
        class="rounded-full h-24 w-24"
      />
    </VCol>
    <VCol class="font-bold text-2xl px-6"
      >Start Your <br />
      Invesment Journey <br />With Us</VCol
    >
    <div class="d-flex align-center mb-2 px-6">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="green"
        class="h-5 w-5"
      >
        <path
          d="M9.9997 15.1709L19.1921 5.97852L20.6063 7.39273L9.9997 17.9993L3.63574 11.6354L5.04996 10.2212L9.9997 15.1709Z"
        ></path>
      </svg>
      <span class="ms-3">Bank Account number and IFSC </span>
    </div>
    <div class="d-flex align-center mb-2 px-6">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="green"
        class="h-5 w-5"
      >
        <path
          d="M9.9997 15.1709L19.1921 5.97852L20.6063 7.39273L9.9997 17.9993L3.63574 11.6354L5.04996 10.2212L9.9997 15.1709Z"
        ></path>
      </svg>
      <span class="ms-3">Bank Account number and IFSC </span>
    </div>
    <div class="d-flex align-center mb-2 px-6">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="green"
        class="h-5 w-5"
      >
        <path
          d="M9.9997 15.1709L19.1921 5.97852L20.6063 7.39273L9.9997 17.9993L3.63574 11.6354L5.04996 10.2212L9.9997 15.1709Z"
        ></path>
      </svg>
      <span class="ms-3">Bank Account number and IFSC </span>
    </div>
    <div class="d-flex align-center mb-2 px-6">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="green"
        class="h-5 w-5"
      >
        <path
          d="M9.9997 15.1709L19.1921 5.97852L20.6063 7.39273L9.9997 17.9993L3.63574 11.6354L5.04996 10.2212L9.9997 15.1709Z"
        ></path>
      </svg>
      <span class="ms-3">Bank Account number and IFSC </span>
    </div>
    <div class="d-flex align-center mb-2 px-6">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="green"
        class="h-5 w-5"
      >
        <path
          d="M9.9997 15.1709L19.1921 5.97852L20.6063 7.39273L9.9997 17.9993L3.63574 11.6354L5.04996 10.2212L9.9997 15.1709Z"
        ></path>
      </svg>
      <span class="ms-3">Bank Account number and IFSC </span>
    </div>
    <VCol
      cols="12"
      class="px-5 pt-10"
    >
      <VBtn
        block
        type="submit"
        to="/pandetails"
      >
        OPEN ACCOUNT
      </VBtn>
    </VCol>
  </VRow>
</template>
<style lang="scss">
</style>
