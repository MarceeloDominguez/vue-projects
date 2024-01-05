<script setup lang="ts">
defineProps({
  title: {
    type: String,
    required: true,
  },
  dynamicFor: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <label
    :for="dynamicFor"
    class="text-slate-100 text-sm font-bold leading-tight tracking-normal mb-2"
    >{{ title }}</label
  >
</template>
