<script setup lang="ts">
import IconStarPlus from "@/components/icons/IconStarPlus.vue";
import IconEye from "@/components/icons/IconEye.vue";
import IconMerge from "@/components/icons/IconMerge.vue";

defineProps<{ title: string; content: string; }>();
</script>

<template>
  <div class="card">
    <h5>{{ title }}</h5>
    <p>{{ content }}</p>
    <div class="project-buttons">
      <IconStarPlus />
      <IconEye />
      <IconMerge />
    </div>
  </div>
</template>

<style scoped>
</style>