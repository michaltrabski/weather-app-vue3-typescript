<template>
  <div class="flex flex-col min-h-screen font-Roboto bg-weather-primary">
    <Sitenavigation />
    <RouterView />
  </div>
</template>

<script setup lang="ts">
import { RouterView } from 'vue-router';
import Sitenavigation from '@/components/SiteNavigation.vue';
</script>

 