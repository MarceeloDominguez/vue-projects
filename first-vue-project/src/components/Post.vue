<script setup lang="ts">
import type { PostModel } from "../models/post.model";

const { post } = defineProps(["post"]) as { post: PostModel };
</script>

<template>
  <div class="p-4 rounded-lg shadow-md border-b-4 border-b-green-500">
    <h1 class="truncate text-slate-100 uppercase font-bold text-[18px]">
      {{ post.title }}
    </h1>
    <p class="line-clamp-4 text-slate-100/50 py-1">{{ post.body }}</p>
  </div>
</template>
../interface/post
