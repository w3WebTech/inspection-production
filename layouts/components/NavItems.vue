<script lang="ts" setup>
import VerticalNavGroup from '@layouts/components/VerticalNavGroup.vue'
import VerticalNavLink from '@layouts/components/VerticalNavLink.vue'
import VerticalNavSectionTitle from '@/@layouts/components/VerticalNavSectionTitle.vue'
</script>

<template>
  <VerticalNavLink
    :item="{
      title: 'Inspection',
      to: '/mobileAppPage1',
    }"
  />
</template>
