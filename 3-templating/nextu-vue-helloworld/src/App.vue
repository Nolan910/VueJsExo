<script setup lang="ts">
import AsideView from './components/layouts/AsideView.vue'
import HeaderView from './components/layouts/HeaderView.vue'
import NavView from './components/layouts/NavView.vue'
import HomeProjectView from './views/HomeProjectView.vue'
</script>
<template>
  <AsideView />
  <main>
    <HeaderView />
    <NavView />
    <HomeProjectView />
  </main>
</template>
<style scoped></style>
