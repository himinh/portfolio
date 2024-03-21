<script setup lang="ts">
import { useRoute } from 'vue-router';

const route = useRoute();
const { slug } = route.params;
</script>

<template>
  <article
    class="prose dark:prose-invert prose-pre:bg-white dark:prose-pre:bg-gray-800 prose-pre:text-gray-700 darK:prose-pre:text-gray-300"
  >
    <ContentDoc />
  </article>
</template>

<style lang="css" scoped></style>
