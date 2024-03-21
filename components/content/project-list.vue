<script setup lang="ts">
const { pending, error, data } = await useFetch<any>(
  'https://api.github.com/users/piotr-jura-udemy/repos'
);

const repos = computed(() =>
  data.value
    .filter((repo: any) => repo.description)
    .sort((a: any, b: any) => b.stargazers_count - a.stargazers_count)
);
</script>

<template>
  <div class="not-prose">
    <section v-if="pending">Loading...</section>
    <section v-else-if="error">Something went wrong....</section>
    <section v-else>
      <ul class="grid grid-cols-1 gap-4">
        <li
          v-for="repo in repos"
          :key="repo.id"
          class="border border-gray-200 rounded-sm p-4 hover:bg-gray-100 font-mono"
        >
          <a :href="repo.html_url" target="_blank">
            <div class="flex items-center justify-between">
              <div class="font-semibold">{{ repo.name }}</div>
              <div>{{ repo.stargazers_count }} ★</div>
            </div>

            <div class="text-sm">{{ repo.description }}</div>
          </a>
        </li>
      </ul>
    </section>
  </div>
</template>

<style lang="css" scoped></style>
