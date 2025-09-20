<script setup>
import PostItem from '@/components/PostItem.vue';
import MyWrapper from '@/components/MyWrapper.vue';
import { usePostsStore } from '@/stores/post';

const postStore = usePostsStore(); // gamiton nato consistent ang lowercase "postStore"
</script>

<template>
  <MyWrapper>
    <div v-for="post in postStore.sorted" :key="post.id">
      <PostItem :post="post" />
    </div>
  </MyWrapper>
</template>
