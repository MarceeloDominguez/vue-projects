<script setup lang="ts">
import { computed, onMounted, ref } from "vue";
import Post from "./components/Post.vue";
import Pagination from "./components/Pagination.vue";
import Loading from "./components/Loading.vue";
import type { PostModel } from "./models/post.model";

const posts = ref<PostModel[]>([]);
const postXpage: number = 10;
const start = ref<number>(0);
const end = ref<number>(postXpage);
const loading = ref<boolean>(false);

onMounted(async () => {
  loading.value = true;
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    posts.value = await res.json();
  } catch (error) {
    console.log(error);
  } finally {
    setTimeout(() => (loading.value = false), 500);
  }
});

const next = () => {
  start.value += postXpage;
  end.value += postXpage;
};

const prev = () => {
  start.value -= postXpage;
  end.value -= postXpage;
};

const maxLength = computed(() => posts.value.length);
const paginatePage = computed(() => posts.value.slice(start.value, end.value));
</script>

<template>
  <Loading v-if="loading" />
  <div v-else class="bg-slate-900 min-h-screen">
    <header
      class="container m-auto flex items-center justify-center pb-2 pt-5 gap-4"
    >
      <h1 class="text-slate-100 font-bold text-[30px]">Pagination with</h1>
      <img src="./assets/logo.svg" class="w-10 h-10 object-contain" />
    </header>
    <main class="container m-auto">
      <section
        class="grid lg:grid-cols-4 md:grid-cols-3 grid-cols-1 gap-4 py-4 px-4"
      >
        <Post v-for="post in paginatePage" :key="post.id" :post="post" />
      </section>
      <section>
        <Pagination
          @next="next"
          @prev="prev"
          :start="start"
          :end="end"
          :maxLength="maxLength"
        />
      </section>
    </main>
  </div>
</template>
