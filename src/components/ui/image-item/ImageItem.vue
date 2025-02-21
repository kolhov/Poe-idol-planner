<script setup lang="ts">
defineProps<{
  imageSrc: string
}>()
</script>

<template>
  <img :src="imageSrc" alt="Image" style="width: 100%; height: 100%; object-fit: cover;" />
</template>
