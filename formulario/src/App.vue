<script setup lang="ts">
import Form from "./components/Form.vue";
</script>

<template>
  <main
    class="absolute top-0 z-[-2] h-screen w-screen bg-neutral-950 bg-[radial-gradient(ellipse_80%_80%_at_50%_-20%,rgba(120,119,198,0.3),rgba(255,255,255,0))]"
  >
    <header class="flex justify-center items-center gap-4 py-10">
      <h1 class="text-slate-50 font-bold text-[30px]">Formulario con</h1>
      <img src="./assets//logo.svg" class="size-8" />
    </header>
    <Form />
  </main>
</template>
