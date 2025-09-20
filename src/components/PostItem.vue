<script setup>
import { usePostsStore } from '@/stores/post';

const postStore = usePostsStore() // sigurado nga "postStore" ang variable name
defineProps({
  post: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="post-item">
    <div class="post-header">
      <span class="post-id">POST #{{ post.id }}</span>
      <div class="post-actions">
        <button @click="postStore.deletePost(post.id)" class="del material-icons" title="Delete">delete</button>
        <button class="save material-icons" title="Save">bookmark_border</button>
      </div>
    </div>

    <div class="post-content">
      <h1>{{ post.title }}</h1>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.post-item {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.08);
  margin-bottom: 1.5rem;
  overflow: hidden;
  transition: transform 0.2s ease, box-shadow 0.2s ease;

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(0,0,0,0.12);
  }
}

.post-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1.25rem;
  background: linear-gradient(90deg, #f015bd, #ff85d2);
  color: #fff;
  font-weight: 500;
  font-size: 1rem;

  .post-id {
    font-weight: 700;
  }

  .post-actions {
    display: flex;
    gap: 0.5rem;

    button {
      border: none;
      border-radius: 50%;
      width: 32px;
      height: 32px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 18px;
      cursor: pointer;
      transition: all 0.2s ease;

      &.del {
        background: #fff;
        color: #ef4444;

        &:hover {
          background: #ef4444;
          color: #fff;
        }
      }

      &.save {
        background: #fff;
        color: #14a841;

        &:hover {
          background: #14a841;
          color: #fff;
        }
      }
    }
  }
}

.post-content {
  padding: 1rem 1.25rem;

  h1 {
    font-size: 1.25rem;
    font-weight: 700;
    color: #1e293b;
    margin-bottom: 0.5rem;
    text-transform: capitalize;
  }

  p {
    font-size: 1rem;
    line-height: 1.6;
    color: #475569;
    white-space: pre-line;
  }
}
</style>
