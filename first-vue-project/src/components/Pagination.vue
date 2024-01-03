<script setup lang="ts">
type MyComponentProps = {
  start: number;
  end: number;
  maxLength: number;
};

//defineProps(["start", "end", "maxLength"]);
const props = defineProps<MyComponentProps>();
const emit = defineEmits(["next", "prev"]);
</script>

<template>
  <div class="lg:py-4 py-3 flex justify-center gap-4 lg:mt-24">
    <button
      class="bg-slate-700 px-6 py-2 rounded-md shadow-md text-slate-100 font-semibold text-sm"
      @click="emit('prev')"
      :disabled="props.start === 0"
      :class="{ 'opacity-50': props.start === 0 }"
    >
      Prev
    </button>
    <button
      class="bg-slate-700 px-6 py-2 rounded-md shadow-md text-slate-100 font-semibold text-sm"
      @click="emit('next')"
      :disabled="props.end >= props.maxLength"
      :class="{ 'opacity-50': props.end >= props.maxLength }"
    >
      Next
    </button>
  </div>
</template>
