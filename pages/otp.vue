<script lang="ts" >
export default {
  data() {
    return {
      timerValue: 30, // Initial time in seconds
      intervalId: null,
      isRunning: false,
      emailAddress: '',
      isValidEmail: false,
      isError: false,
      isMobileNumberValid: false,
      mobileNumber: '',
      otpLength: 6, // length of the OTP
      otpTimer: 0, // timer for OTP resend
      otpInterval: null,
      otp6: null,
    }
  },
  mounted() {
    this.startOtpTimer()
    this.otp6 == '6' ?? this.$router.push('/mainpage')
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
    startOtpTimer() {
      this.otpTimer = 30 // set timer to 60 seconds
      this.otpInterval = setInterval(() => {
        this.otpTimer -= 1
        if (this.otpTimer <= 0) {
          clearInterval(this.otpInterval)
        }
      }, 1000)
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
        <VRow class="py-4 px-2">
          <VCol
            cols="3"
            md="2"
            class="px-6"
          >
            <img
              src="@images/phonepay.png"
              alt=""
              class="h-10 w-10"
          /></VCol>
          <VCol
            cols="1"
            md="1"
            class="px-6"
          >
            <IconBtn class="">
              <VIcon icon="ri-arrow-right-line" />
            </IconBtn>
          </VCol>
          <VCol
            cols="4"
            md="2"
            class="px-6"
          >
            <img
              src="@/public/download.png"
              alt=""
              class="h-10 w-10"
          /></VCol>
        </VRow>
        <VCol class="font-bold text-lg text-black px-5">Verify Your Mobile number</VCol>

        <VCol
          cols="12"
          class="px-5"
        >
          We need to verify your phonepe accountId proceed</VCol
        >
        <VCol class="font-bold text-black px-5"> Enter OTP Send to 6374586149</VCol>
        <VCol cols="12">
          <OtpInput />
        </VCol> </VCard></VCol
  ></VRow>
</template>
<style lang="scss">
</style>
