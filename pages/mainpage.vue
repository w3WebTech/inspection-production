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
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCol class="py-1">
        <span class="text-[#8C57FF] font-bold text-2xl pr-1"> Share</span>
        <span class="text-3xl font-bold text-success">.</span>
        <span class="text-[#8C57FF] font-bold text-2xl px-2">Market</span></VCol
      >
      <VCol class="font-bold text-lg text-black py-1"
        >Open Your Free Demat & <br />
        Trading Account</VCol
      >
      <VCol class="py-1"> <VLabel>Trade on Stocks ETF's and wealth</VLabel></VCol>
      <VCol
        v-for="data in this?.solidCardData"
        :key="data"
        class="py-1"
      >
        <VCard
          :color="data?.cardBg"
          class="absolute top-6"
        >
          <img
            src="@/public/new.jpeg"
            alt=""
            class=""
          />
        </VCard>
      </VCol>
      <VCol>
        <VCard class="static">
          <div class="border-b-2 text-black text-[14px] px-2 py-2">Things To Keep Money</div>
          <div class="d-flex align-center mb-6 mt-3 px-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="#8C57FF"
              class="h-5 w-5"
            >
              <path
                d="M20 22H4C3.44772 22 3 21.5523 3 21V3C3 2.44772 3.44772 2 4 2H20C20.5523 2 21 2.44772 21 3V21C21 21.5523 20.5523 22 20 22ZM7 6V10H11V6H7ZM7 12V14H17V12H7ZM7 16V18H17V16H7ZM13 7V9H17V7H13Z"
              ></path>
            </svg>
            <span class="ms-3">PAN and Adhar number</span>
          </div>
          <div class="d-flex align-center mb-6 px-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="#8C57FF"
              class="h-7 w-7"
            >
              <path
                d="M12 6C12 4.46329 12.5777 3.06151 13.5278 2H6C5.44772 2 5 2.44772 5 3V21C5 21.5523 5.44772 22 6 22H18C18.5523 22 19 21.5523 19 21V11.917C18.6748 11.9716 18.3407 12 18 12C14.6863 12 12 9.31371 12 6ZM12 17C12.5523 17 13 17.4477 13 18C13 18.5523 12.5523 19 12 19C11.4477 19 11 18.5523 11 18C11 17.4477 11.4477 17 12 17ZM22 6H19V2H17V6H14L18 10L22 6Z"
              ></path>
            </svg>
            <span class="ms-3">Any Mobile Number linked to Adhar to receive OTP</span>
          </div>
          <div class="d-flex align-center mb-2 px-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="#8C57FF"
              class="h-5 w-5"
            >
              <path
                d="M2 20H22V22H2V20ZM4 12H6V19H4V12ZM9 12H11V19H9V12ZM13 12H15V19H13V12ZM18 12H20V19H18V12ZM2 7L12 2L22 7V11H2V7ZM12 8C12.5523 8 13 7.55228 13 7C13 6.44772 12.5523 6 12 6C11.4477 6 11 6.44772 11 7C11 7.55228 11.4477 8 12 8Z"
              ></path>
            </svg>
            <span class="ms-3">Bank Account number and IFSC </span>
          </div>
          <VCol
            cols="12"
            class="py-3"
          >
            <VBtn
              block
              type="submit"
              to="/addEmail"
            >
              OPEN FREE ACCOUNT
            </VBtn>
          </VCol>
        </VCard>
      </VCol>
    </VCol>
  </VRow>
</template>
<style lang="scss">
</style>
