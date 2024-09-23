<script lang="ts" setup>
import NavItems from '@/layouts/components/NavItems.vue'
import VerticalNavLayout from '@layouts/components/VerticalNavLayout.vue'

// Components
import Footer from '@/layouts/components/Footer.vue'
import NavbarThemeSwitcher from '@/layouts/components/NavbarThemeSwitcher.vue'
import UserProfile from '@/layouts/components/UserProfile.vue'
import { ref } from 'vue'
import { onMounted } from 'vue'
import { useRoute } from 'vue-router'
const empName = ref('')
const empId = ref('')

onMounted(() => {
  const route = useRoute()
  empName.value = route.query.employeeName ? route.query.employeeName : 'GZ10219'
  console.log(empName.value, ' empName')
  empId.value = route.query.employeeId ? route.query.employeeId : 'GZ10219'
  console.log(empId.value, ' empId')
})

// import { userDataStore } from '~/stores/tableData'
// const userStore = userDataStore()
</script>

<template>
  <VerticalNavLayout>
    <!-- 👉 navbar -->
    <template #navbar="{ toggleVerticalOverlayNavActive }">
      <div class="d-flex h-100 align-center prof">
        <!-- 👉 Vertical nav toggle in overlay mode -->
        <IconBtn
          class="ms-n3 d-lg-none"
          @click="toggleVerticalOverlayNavActive(true)"
        >
          <VIcon icon="ri-menu-line" />
        </IconBtn>

        <!-- 👉 Search -->

        <VSpacer />
        <div class="px-4 font-bold py-1 text-sm">
          <div>{{ empName ? empName : 'hh' }}</div>
          <div>{{ empId ? empId : 'hh' }}</div>
        </div>
        <!-- <NavbarThemeSwitcher class="me-2" /> -->
        <UserProfile />
      </div>
    </template>

    <template #vertical-nav-header="{ toggleIsOverlayNavActive }">
      <NuxtLink
        to="/"
        class="app-logo app-title-wrapper"
      >
        <v-img
          :width="207"
          aspect-ratio="16/9"
          cover
          src="https://powerstocks.gwcindia.in/Img/Power%20Stocks%20Logo%20Final%20Feb%202024%201.jpg"
        ></v-img>
      </NuxtLink>

      <IconBtn
        class="d-block d-lg-none"
        @click="toggleIsOverlayNavActive(false)"
      >
        <VIcon icon="ri-close-line" />
      </IconBtn>
    </template>

    <template #vertical-nav-content>
      <NavItems />
    </template>

    <!-- 👉 Pages -->
    <slot />

    <!-- 👉 Footer -->
    <template #footer>
      <Footer />
    </template>
  </VerticalNavLayout>
</template>

<style lang="scss" scoped>
.meta-key {
  border: thin solid rgba(var(--v-border-color), var(--v-border-opacity));
  border-radius: 6px;
  block-size: 1.5625rem;
  line-height: 1.3125rem;
  padding-block: 0.125rem;
  padding-inline: 0.25rem;
}

.prof {
  z-index: 1000;
}

.app-logo {
  display: flex;
  align-items: center;
  column-gap: 0.75rem;

  .app-logo-title {
    font-size: 1.25rem;
    font-weight: 500;
    line-height: 1.75rem;
    text-transform: uppercase;
  }
}
</style>
