<script setup lang="ts">
//defineProps(["inputId", "modelValue"]);

type TYPE_INPUT = "text" | "email" | "password" | "number" | "date";

defineProps({
  inputId: {
    type: String,
    required: true,
  },
  modelValue: {
    type: String,
    required: true,
  },
  placeholder: {
    type: String,
    required: true,
  },
  type: {
    type: String as () => TYPE_INPUT,
    default: "text",
  },
});
const emits = defineEmits(["update:modelValue"]);

function updateModelValue(event: Event): void {
  emits("update:modelValue", (event.target as HTMLInputElement).value);
}
</script>

<template>
  <input
    :id="inputId"
    class="text-slate-50 w-full h-10 focus:outline-none border-none bg-slate-600 font-normal flex items-center px-4 text-sm rounded border shadow"
    :placeholder="placeholder"
    :value="modelValue"
    @input="updateModelValue"
    :type="type"
  />
</template>
