<script lang="ts" setup>
import type { PostDetails } from "~/data/posts";
import { getPostDetailsUrl } from "~/data/posts";
const postSlug = useParam("post");
const { data: post } = await useFetch<PostDetails>(getPostDetailsUrl(postSlug));
</script>

<template>
  <template v-if="post">
    <main>
      <h1>
        {{ post?.title }}
        <CategoryLink :category="post.category" />
      </h1>
      <RenderMarkdown :source="post.content" />
    </main>
  </template>
</template>

<style></style>
