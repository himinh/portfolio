<script setup lang="ts"></script>

<template>
  <nav class="font-mono">
    <ul class="flex space-x-4">
      <li><NuxtLink to="/" class="link">Home</NuxtLink></li>

      <li>
        <NuxtLink to="/blog" class="link">Blogs</NuxtLink>
      </li>

      <li>
        <NuxtLink to="/about" class="link">About</NuxtLink>
      </li>

      <li>
        <NuxtLink to="/projects" class="link">Projects</NuxtLink>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.link {
  @apply p-1 hover:bg-gray-200;
}
</style>
