<script setup>
import Wrapper from '@/components/Wrapper.vue';
</script>

<template>
  <Wrapper>
    <form>
      <h3>Add a New Post</h3>
      <div>
        <label>Post Title</label>
        <input type="text" placeholder="Enter your title..." />
      </div>
      <div>
        <label>Post Content</label>
        <textarea rows="5" placeholder="Write something..."></textarea>
      </div>
      <div>
        <button type="submit">✨ Publish</button>
      </div>
    </form>
  </Wrapper>
</template>

<style lang="scss" scoped>
form {
  background: #d73995;
  padding: 2rem 2.5rem;
  width: 100%;
  max-width: 550px;
  margin: 2rem auto;
  border-radius: 1rem;
  box-shadow: 0 8px 25px rgba(36, 31, 31, 0.08);
  font-family: 'Poppins', sans-serif;

  h3 {
    margin-bottom: 1.5rem;
    font-size: 1.6rem;
    font-weight: 600;
    color: #222;
    text-align: center;
    letter-spacing: 0.5px;
  }

  div {
    margin-bottom: 1.5rem;

    label {
      display: block;
      margin-bottom: 0.6rem;
      font-weight: 500;
      color: #242020;
      font-size: 0.95rem;
    }

    input,
    textarea {
      width: 100%;
      padding: 0.9rem 1rem;
      border: 1px solid #ddd;
      border-radius: 0.75rem;
      font-size: 1rem;
      background-color: #f9f9fb;
      transition: all 0.3s ease;

      &:focus {
        border-color: #121032;
        background-color: #fff;
        outline: none;
        box-shadow: 0 0 0 4px rgba(108, 99, 255, 0.15);
      }

      &::placeholder {
        color: #aaa;
        font-size: 0.9rem;
      }
    }

    button {
      width: 100%;
      padding: 0.9rem;
      background: linear-gradient(135deg, #53517f, #ea138d);
      color: #141313;
      font-size: 1.05rem;
      font-weight: 600;
      border: none;
      border-radius: 0.75rem;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.3s ease;

      &:hover {
        transform: translateY(-2px);
        box-shadow: 0 8px 15px rgba(91, 86, 192, 0.3);
      }

      &:active {
        transform: translateY(0);
        box-shadow: none;
      }
    }
  }
}
</style> 