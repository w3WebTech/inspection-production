<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {
      fileInput: null as HTMLInputElement | null,
      images: null as string | null,
      isDialogVisible: false,
    }
  },
  methods: {
    openFileInput() {
      if (this.fileInput) {
        this.fileInput.click()
      }
    },
    handleFileUpload(event: Event) {
      const input = event.target as HTMLInputElement
      if (input.files && input.files[0]) {
        const file = input.files[0]
        const reader = new FileReader()
        reader.onload = e => {
          if (typeof e.target?.result === 'string') {
            this.images = e.target.result
          }
        }
        reader.readAsDataURL(file)
      }
    },
  },
  mounted() {
    this.fileInput = this.$refs.fileInput as HTMLInputElement
  },
})
</script>

<template>
  <VRow>
    <VCol
      cols="12"
      md="6"
    >
      <VCol class="font-bold text-lg py-1">Upload Your Pan</VCol>
      <VCol class="py-1">Proof of PAN is needed for all investments in India</VCol>
      <VCol
        cols="12"
        class=""
      >
        <div class="border border-gray rounded-md h-40">
          <VCol @click="openFileInput">
            <div>
              <div
                v-if="!images"
                class="d-flex justify-center items-center text-center py-10"
              >
                <img
                  src="@/public/upload.png"
                  alt=""
                  class="h-10 w-10"
                />
              </div>
              <div v-else>
                <img
                  :src="images"
                  alt=""
                />
              </div>
            </div>
          </VCol>
          <input
            type="file"
            ref="fileInput"
            id="fileInput"
            @change="handleFileUpload"
            hidden
          />
        </div>
      </VCol>
      <VCol class="text-xs">
        <VAlert
          border="start"
          border-color="warning"
          class="text-xs"
        >
          Please click a horizontal photo of the PAN card and ensure that your name and PAN number are clearly visible.
        </VAlert>
      </VCol>
      <VCol
        cols="12"
        class=""
      >
        <VBtn
          block
          type="submit"
          @click="isDialogVisible = true"
        >
          PROCEED
        </VBtn>
      </VCol>

      <VDialog
        v-model="isDialogVisible"
        width="500"
      >
        <!-- Dialog Content -->
        <VCard>
          <DialogCloseBtn
            variant="text"
            size="default"
            @click="isDialogVisible = false"
          />

          <VCol>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="red"
              class="h-12 w-12"
            >
              <path
                d="M12 22C6.47715 22 2 17.5228 2 12C2 6.47715 6.47715 2 12 2C17.5228 2 22 6.47715 22 12C22 17.5228 17.5228 22 12 22ZM11 15V17H13V15H11ZM11 7V13H13V7H11Z"
              ></path>
            </svg>
          </VCol>
          <VCol class="font-bold text-lg py-1">PAN Verification Failed</VCol>
          <VCol class="py-1 align-center text-sm"
            >The image you've uploaded is not of a valid PAN card. Please share the image of a valid PAN card</VCol
          >
          <VCol
            cols="12"
            class="pt-5"
          >
            <VBtn
              block
              type="submit"
              @click="isDialogVisible = true"
              to="/successmessage"
            >
              TRY AGAIN
            </VBtn>
          </VCol>
        </VCard>
      </VDialog>
    </VCol></VRow
  >
</template>

<style lang="scss">
.v-alert__content {
  font-size: 12px !important;
  font-weight: 200 !important;
  line-height: 15px !important;
}
</style>
