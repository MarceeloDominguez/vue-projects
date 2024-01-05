<script setup lang="ts">
type TYPE_CLASS = "bg-green-700" | "bg-green-800" | "bg-green-900";
type TYPE_BUTTON = "button" | "submit" | "reset";

defineProps({
  title: {
    type: String,
    required: true,
  },
  class: {
    type: String as () => TYPE_CLASS,
    default: "bg-green-600",
  },
  type: {
    type: String as () => TYPE_BUTTON,
    default: "button",
  },
});
</script>

<template>
  <button
    :class="class"
    class="h-10 w-full rounded shadow text-slate-50 font-bold text-sm"
    :type="type"
  >
    {{ title }}
  </button>
</template>
