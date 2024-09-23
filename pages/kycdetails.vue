<script lang="ts" >
import Datepicker from 'vue3-datepicker'
export default {
  components: {
    Datepicker,
  },
  data() {
    return {
      selectedDateTime: null,
      language: 'en',
      selectedgenderButton: 'FEMALE',
      selectedstatusButton: 'UN-MARRIED',
      selectedparentButton: 'FATHER',
    }
  },
  mounted() {
    const buttons = [
      this.$refs.genderButton1,
      this.$refs.genderButton2,
      this.$refs.genderButton3,
    ] as HTMLButtonElement[]
    const statusbutton = [this.$refs.marrietalStatusButton1, this.$refs.marrietalStatusButton2] as HTMLButtonElement[]
    const parentsButton = [this.$refs.parentsButton1, this.$refs.parentsButton2] as HTMLButtonElement[]

    buttons.forEach((button: HTMLButtonElement) => {
      button.addEventListener('click', () => {
        buttons.forEach(btn => btn.classList.remove('selected'))
        button.classList.add('selected')
        this.selectedgenderButton = button
        console.log('Selected button value:', this.selectedgenderButton.textContent.trim())
      })
    })
    statusbutton.forEach((button: HTMLButtonElement) => {
      button.addEventListener('click', () => {
        statusbutton.forEach(btn => btn.classList.remove('selected'))
        button.classList.add('selected')
        this.selectedstatusButton = button
        console.log('Selected button value:', this.selectedstatusButton.textContent.trim())
      })
    })
    parentsButton.forEach((button: HTMLButtonElement) => {
      button.addEventListener('click', () => {
        parentsButton.forEach(btn => btn.classList.remove('selected'))
        button.classList.add('selected')
        this.selectedparentButton = button
        console.log('Selected button value:', this.selectedparentButton.textContent.trim())
      })
    })
  },
  method() {},
}
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCard class="px-2">
        <VCol class="px-3">KYC detail(1/3)</VCol>
        <VCol class="font-bold text-lg pt-1">Let's Get To Know You</VCol>
        <VCol class="px-3 py-1">This is required to complete your KYC and securely open your demat account</VCol>
        <VCol>
          <VLabel class="font-bold">Gender</VLabel>
        </VCol>
        <VRow class="px-3">
          <VCol>
            <button
              ref="genderButton1"
              class="gender-button"
            >
              MALE
            </button>
            <button
              ref="genderButton2"
              class="gender-button"
            >
              FEMALE
            </button>
            <button
              ref="genderButton3"
              class="gender-button"
            >
              TRANSGENDER
            </button>
          </VCol>
        </VRow>

        <VCol>
          <VLabel class="font-bold">Marital Status</VLabel>
        </VCol>
        <VRow class="px-3">
          <VCol>
            <button
              ref="marrietalStatusButton1"
              class="gender-button"
            >
              UN-MARRIED
            </button>
            <button
              ref="marrietalStatusButton2"
              class="gender-button"
            >
              MARRIED
            </button>
          </VCol></VRow
        >
        <VCol>
          <VLabel class="font-bold">Occupation</VLabel>
        </VCol>
        <VCol
          ><VAutocomplete
            :items="items"
            placeholder="Select Occupation"
        /></VCol>
        <VCol>
          <VLabel class="font-bold">Date Of Birth</VLabel>
        </VCol>
        <VCol class="">
          <datepicker
            v-model="selectedDateTime"
            format="yyyy-MM-dd HH:mm:ss"
            :language="language"
            class="datepick"
        /></VCol>
        <VCol>
          <VLabel class="font-bold">Parents Name</VLabel>
        </VCol>
        <VRow class="px-3">
          <VCol>
            <button
              ref="parentsButton1"
              class="gender-button"
            >
              FATHER
            </button>
            <button
              ref="parentsButton2"
              class="gender-button"
            >
              MOTHER
            </button></VCol
          ></VRow
        >
        <VCol> <VTextField /></VCol>
        <VCol
          cols="12"
          class="pb-20"
        >
          <VBtn
            block
            type="submit"
            to="/kycdetails2"
          >
            PROCEED
          </VBtn>
        </VCol>
      </VCard></VCol
    ></VRow
  >
</template>
<style lang="scss">
.gender-button {
  padding: 4px 8px;
  border: 1px solid #bfbdc4;
  margin-right: 6px;
  border-radius: 4px;
  border-color: #bfbdc4;
  font-size: 0.875rem;
  font-weight: medium;

  background-color: white;
  color: #bfbdc4;
  &:hover {
    border: 1px solid #9c74f0;
    background-color: #9c74f0;
    color: white; /* Adjust hover background color */
  }
}

/* Styles for the selected gender button */
.gender-button.selected {
  border: 1px solid #9c74f0;
  background-color: #9c74f0; /* Adjust selected background color */
  color: white;
}
.datepick {
  padding: 10px 8px;
  border: 1px solid #bfbdc4;
  margin-right: 6px;
  border-radius: 4px;
  border-color: #bfbdc4;
  font-size: 0.875rem;
  font-weight: medium;
  width: 100%;

  background-color: white;
  color: #bfbdc4;
}
</style>
