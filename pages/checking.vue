<template>
  <VCard>
    <VRow>
      <VCol
        cols="12"
        md="4"
        :class="$vuetify.display.smAndDown ? 'border-b' : 'border-e'"
      >
        <VCardText>
          <!-- 👉 Stepper -->
          <AppStepper
            @step-changed="handleStepChanged"
            v-model:current-step="currentStep"
            direction="vertical"
            :items="numberedSteps"
          />
        </VCardText>
      </VCol>
      <!-- 👉 Stepper content -->
      <VCol
        cols="12"
        md="8"
      >
        <VCardText>
          <VForm>
            <VWindow
              class="disable-tab-transition"
              v-if="currentStep == 0"
            >
              <VWindowItem><FirstStep /></VWindowItem>
            </VWindow>
            <VWindow
              class="disable-tab-transition"
              v-if="currentStep == 1"
            >
              <VWindowItem><selfie /></VWindowItem>
            </VWindow>
            <VWindow
              class="disable-tab-transition"
              v-if="currentStep == 2"
            >
              <VWindowItem><pandetails /></VWindowItem>
            </VWindow>
            <VWindow
              class="disable-tab-transition"
              v-if="currentStep == 3"
            >
              <VWindowItem>fdss</VWindowItem>
            </VWindow>

            <div class="d-flex flex-wrap gap-4 justify-sm-space-between justify-center mt-8 pl-5">
              <VBtn
                color="secondary"
                variant="outlined"
                :disabled="currentStep === 0"
                @click="currentStep--"
              >
                <VIcon
                  icon="ri-arrow-left-line"
                  start
                  class="flip-in-rtl"
                />
                Previous
              </VBtn>

              <VBtn
                v-if="numberedSteps.length - 1 === currentStep"
                color="success"
                append-icon="ri-check-line"
              >
                Submit
              </VBtn>
              <VBtn
                v-else
                @click="currentStep++"
              >
                Next
                <VIcon
                  icon="ri-arrow-right-line"
                  end
                  class="flip-in-rtl"
                />
              </VBtn>
            </div>
          </VForm>
        </VCardText>
      </VCol>
    </VRow>
  </VCard>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {
      currentStep: 0,
      numberedSteps: ['Step 1', 'Step 2', 'Step 3'], // Replace with your step names
    }
  },
  methods: {
    handleStepChanged(newStepValue: number) {
      console.log(newStepValue, 'newStepValue')
      this.currentStep = newStepValue
      // Update your application logic based on the new step value here
    },
  },
})
</script>
