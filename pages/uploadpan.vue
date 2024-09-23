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
    >
      <VCard>
        <VCol class="font-bold text-lg py-1">Fill Your PAN Details</VCol>
        <VCol>proof of PAN is needed for all investments in India</VCol>
        <VTextarea
          type="file"
          id="imageInput"
          ref="fileInput"
        />
        <!-- @change="handleImageUpload" -->
      </VCard>
    </VCol>
  </VRow>
</template>
<style lang="scss">
</style>
