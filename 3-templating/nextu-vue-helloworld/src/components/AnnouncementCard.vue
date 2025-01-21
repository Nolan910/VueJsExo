<script setup lang="ts">
defineProps<{ title: string; content: string }>()
</script>

<template>
  <div class="announcement-card">
    <h5>{{ title }}</h5>
    <p>{{ content }}</p>
  </div>
</template>

<style scoped>
.announcement-card {
  background-color: #f9f9f9;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

h5 {
  margin-bottom: 0.5rem;
  font-size: 1.25rem;
}

p {
  font-size: 1rem;
  color: #555;
}
</style>