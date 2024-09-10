<script setup lang="ts">
defineProps<{
  name: string,
  url: string,
}>()
</script>

<template>
  <div class="px-4 -mx-2 pt-2">
    <a class="font-mono opacity-75 hover:opacity-100" :href="url" target="_blank">{{ name }}</a>
  </div>
</template>
