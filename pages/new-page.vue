<script lang="ts" setup>
const toggleCheckbox1 = ref(false)
const toggleCheckbox2 = ref(false)
const toggleCheckbox3 = ref(false)
const toggleCheckbox4 = ref(false)
const toggleCheckbox5 = ref(false)
const toggleCheckbox6 = ref(false)
const isDialogVisible = ref(true)
const skill = ref(20)
</script>

<template>
  <VCol
    cols="12"
    md="6"
    class="layout-page-content1"
  >
    <VCard class="px-4 py-4">
      <VCheckbox
        v-model="toggleCheckbox1"
        label="Get influencers responces by sharing your offer."
      />
      <VCheckbox
        v-model="toggleCheckbox2"
        label="Discover influencers through a search with filters."
      />
      <VCheckbox
        v-model="toggleCheckbox3"
        label="Run campaigns by sending free product samples and oofering promo codes."
      />
      <VCheckbox
        v-model="toggleCheckbox4"
        label="Connect with shopify/Magento/WooCommerce and find influencers who have ordered from you."
      />
      <VCheckbox
        v-model="toggleCheckbox5"
        label="Explore your competitors ,their strategies ,and find inspiring advertising insights."
      />
      <VCheckbox
        v-model="toggleCheckbox6"
        label="Verify the influencers you've already found."
      />
    </VCard>
  </VCol>

  <VLabel class="py-3 font-bold layout-page-content1">Additional comments</VLabel>

  <VCol
    cols="12"
    md="6"
    class="layout-page-content1"
  >
    <VTextarea
      v-model="textareaValue"
      counter
      placeholder="Tell us more about what you need,want, and hope to do with influencer marketing..."
      class="bg-white h-[135px]"
    />
  </VCol>
  <VCol
    cols="12"
    md="6"
    class="px-3 mb-5"
  >
    <VBtn
      block
      type="submit"
      to="/new-page2"
    >
      skip
    </VBtn>
  </VCol>
  <VCol
    class="fixed bottom-0 bg-white h-[100px] layout-page-content"
    cols="12"
    md="6"
  >
    <div class="demo-space-y px-4">
      <div class="flex justify-end">{{ Math.ceil(skill) }}%</div>
      <VProgressLinear
        v-model="skill"
        color="primary"
        height="20"
      >
      </VProgressLinear>
    </div>
  </VCol>
</template>
<style lang="scss">
.layout-page-content {
}
.layout-page-content1 {
  padding-inline: 1.5rem !important;
}
</style>
