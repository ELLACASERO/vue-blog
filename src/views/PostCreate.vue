<script setup>
import MyWrapper from '@/components/MyWrapper.vue'
import { reactive, computed } from 'vue'
import { useRouter } from 'vue-router'
import { usePostsStore } from '@/stores/post'

const router = useRouter()
const postStore = usePostsStore()

const post = reactive({
  title: '',
  body: ''
})

const isFormInvalid = computed(() => {
  return post.title.trim() === '' || post.body.trim() === ''
})

const handleSubmit = () => {
  postStore.addPost(post)
  router.push({ name: 'home' })
}
</script>

<template>
  <MyWrapper>
    <div class="header">
      <span>Create a New Post</span>
      <RouterLink to="/" class="back-link">
        <span class="material-icons">arrow_back</span>
      </RouterLink>
    </div>

    <div class="content">
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label>Post Title</label>
          <input type="text" v-model="post.title" placeholder="Enter post title" />
        </div>
        <div class="form-group">
          <label>Post Body</label>
          <textarea rows="7" v-model="post.body" placeholder="Write your post here..."></textarea>
        </div>
        <button type="submit" :disabled="isFormInvalid">Add Post</button>
      </form>
    </div>
  </MyWrapper>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1.5rem;
  background: linear-gradient(90deg, #f015a7, #ff85d2);
  color: #fff;
  font-weight: 600;
  font-size: 1.2rem;
  border-radius: 12px 12px 0 0;

  .back-link {
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fff;
    color: #f01598;
    border-radius: 50%;
    width: 36px;
    height: 36px;
    text-decoration: none;
    transition: all 0.2s ease;

    .material-icons {
      font-size: 20px;
    }

    &:hover {
      background: #fce4f0;
    }
  }
}

.content {
  background: #fff;
  padding: 2rem;
  border-radius: 0 0 12px 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.06);

  form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;

      label {
        font-weight: 500;
        color: #1e293b;
      }

      input,
      textarea {
        width: 100%;
        padding: 10px 12px;
        border-radius: 8px;
        border: 1px solid #ddd;
        font-size: 1rem;
        transition: all 0.2s ease;

        &:focus {
          outline: none;
          border-color: #f63bb2;
          box-shadow: 0 0 0 3px rgba(246, 59, 178, 0.2);
        }
      }
    }

    button {
      padding: 12px;
      font-weight: 600;
      font-size: 1rem;
      color: #fff;
      background: #f63bb2;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.2s ease;

      &:hover:not(:disabled) {
        background: #e53992;
      }

      &:disabled {
        background: #f7a1d1;
        cursor: not-allowed;
      }
    }
  }
}
</style>
