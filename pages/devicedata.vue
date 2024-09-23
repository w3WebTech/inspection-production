<template>
  <div>
    <h1>Device Details</h1>
    <p>User Agent: {{ userAgent }}</p>
    <p>Platform: {{ platform }}</p>
    <!-- Add more device details as needed -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      userAgent: '',
      platform: '',
      // Add more properties for other device details if needed
    }
  },
  mounted() {
    this.fetchDeviceDetails()
  },
  methods: {
    fetchDeviceDetails() {
      this.userAgent = navigator.userAgent
      this.platform = navigator.platform
      // Add more properties for other device details if needed
    },
  },
}
</script>
