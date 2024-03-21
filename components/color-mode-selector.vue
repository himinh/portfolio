<script setup lang="ts">
const colorMode = useColorMode();

const modes = ['system', 'light', 'dark'] as const;
const nextModeIcons = {
  system: '🌓',
  light: '🌕',
  dark: '🌑',
};

const nextMode = computed<(typeof modes)[number]>(() => {
  const currentModeIndex = modes.indexOf(
    colorMode.preference as (typeof modes)[number]
  );
  let nextModeIndex = currentModeIndex + 1;

  if (currentModeIndex + 1 == modes.length) {
    nextModeIndex = 0;
  } else {
    nextModeIndex = currentModeIndex + 1;
  }

  return modes[nextModeIndex];
});

const nextModeIcon = computed(() => nextModeIcons[nextMode.value]);

const showNextModelLabel = ref(false);

const toggleMode = () => (colorMode.preference = nextMode.value);
</script>

<template>
  <div class="flex space-x-2 items-center">
    <div v-if="showNextModelLabel" class="text-gray-500 text-xs">
      Change to {{ nextMode }}
    </div>
    <button
      @click="toggleMode"
      @mouseenter="showNextModelLabel = true"
      @mouseleave="showNextModelLabel = false"
      class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-500"
    >
      {{ nextModeIcon }}
    </button>
  </div>
</template>

<style lang="css" scoped></style>
