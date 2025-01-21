<script setup lang="ts">
defineProps<{ username: string; content: string; image: string; }>()
</script>

<template>
  <div class="trend">
    <figure>
      <img
        class="avatar"
        :src="image"
        alt="avatar"
      />
    </figure>
    <div class="trend-details">
      <h6>{{username}}</h6>
      <p>{{content}}</p>
    </div>
  </div>
  <slot />
</template>