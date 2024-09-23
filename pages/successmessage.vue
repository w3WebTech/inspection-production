<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {}
  },
  methods: {},
  setup() {
    const router = useRouter()

    // Automatically navigate to the next page after 10 seconds
    const redirectToNextPage = () => {
      setTimeout(() => {
        router.push('/kycdetails')
      }, 5000)
    }

    return {
      redirectToNextPage,
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.redirectToNextPage()
    })
  },
})
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
      class=""
    >
      <VCard class="d-flex justify-center items-center text-center my-20">
        <VCol>
          <VCol class="d-flex justify-center items-center text-center">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="green"
              class="h-12 w-12"
            >
              <path
                d="M12 22C6.47715 22 2 17.5228 2 12C2 6.47715 6.47715 2 12 2C17.5228 2 22 6.47715 22 12C22 17.5228 17.5228 22 12 22ZM11.0026 16L18.0737 8.92893L16.6595 7.51472L11.0026 13.1716L8.17421 10.3431L6.75999 11.7574L11.0026 16Z"
              ></path>
            </svg>
          </VCol>
          <VCol class="font-bold text-lg py-1">Received Your Documents</VCol>
          <VCol>Proceeding to the next step ...</VCol>
        </VCol>
      </VCard>
    </VCol></VRow
  >
</template>

<style lang="scss">
</style>
