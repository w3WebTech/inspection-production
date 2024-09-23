<template>
  <div class="flex">
    <div class="space-x-4 px-2">
      <input
        v-for="(digit, index) in otpDigits"
        :key="index"
        ref="otpInput"
        v-model="otpInputs[index]"
        @input="focusNextInput(index)"
        @keydown.backspace.prevent="focusPreviousInput(index)"
        class="w-8 h-8 text-center text-sm border border-gray rounded-md"
        maxlength="1"
        type="text"
        pattern="[0-9]"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      otpInputs: ['', '', '', '', '', ''], // Adjust based on the length of your OTP
    }
  },
  computed: {
    otpDigits() {
      return Array.from({ length: 6 }, (_, index) => index + 1) // Adjust based on the length of your OTP
    },
  },
  methods: {
    focusNextInput(index) {
      if (index < this.otpInputs.length - 1) {
        this.$refs.otpInput[index + 1].focus()
      }
    },
    focusPreviousInput(index) {
      if (index > 0) {
        this.$refs.otpInput[index - 1].focus()
      }
    },
    checkAndNavigate() {
      const enteredOTP = this.otpInputs.join('')
      const correctOTP = '123456' // Change this to your desired OTP

      if (enteredOTP === correctOTP && enteredOTP.length == 6) {
        // Navigate to the next page
        this.$router.push('/mainpage') // Adjust the route as per your project
      } else if (enteredOTP.length == 6 && enteredOTP != correctOTP) {
        alert('incorrect OTP')
      } else {
        // Optionally show an error message or handle incorrect OTP
      }
    },
  },
  watch: {
    otpInputs: {
      handler: 'checkAndNavigate',
      deep: true,
    },
  },
}
</script>

<style scoped>
/* Add Tailwind CSS classes here if needed */
</style>
