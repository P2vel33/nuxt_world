<script lang="ts" setup>
import type { CategoryDetails } from "~/data/categories";
import { getCategoryDetailsUrl } from "~/data/categories";

const categorySlug = useParam("category");
const { data: category } = await useFetch<CategoryDetails>(
  getCategoryDetailsUrl(categorySlug)
);
</script>

<template>
  <main>
    <h1>Category: {{ category?.name }}</h1>
    <div>
      <PostCard v-for="post in category?.posts" :key="post.id" :post />
    </div>
  </main>
</template>

<style></style>
