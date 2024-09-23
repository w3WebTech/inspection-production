<template>
  <div>
    <VCol
      v-model="content"
      @click="openFileInput"
    >
      <div v-if="this.images != []">
        <img
          :src="this.images"
          alt=""
        />
      </div>
      <div v-else>
        <img
          src="@/public/upload.png"
          alt=""
        />
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
  <!-- <img
      v-if="imageUrl"
      :src="imageUrl"
      alt="Uploaded Image"
      style="max-width: 100%; max-height: 400px"
    />
  </div> -->
</template>

<script>
export default {
  data() {
    return {
      content: '',
      fileInput: null,
      images: [],
    }
  },
  methods: {
    openFileInput() {
      this.fileInput.click()
      console.log(this.fileInput, '')
    },
    handleFileUpload(event) {
      const file = event.target.files[0]

      const reader = new FileReader()
      reader.onload = e => {
        this.images.push(e.target.result) // Add URL to images array
      }
      console.log(this.images, ' this.images')
      reader.readAsDataURL(file)
    },
    // Handle file upload logic (e.g., on file input change event)
  },
  mounted() {
    this.fileInput = this.$refs.fileInput // Get reference to hidden input
  },
}
</script>

<style scoped>
/* Add your custom styles here */
</style>


