<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts"/>
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostList from "../components/PostList"
import getPost from "../composables/getPosts"

export default {
  name: 'Home',
  setup() {
    const { posts, error, load } = getPost();
    load()
    return { posts, error, load}
  },
  components: {
    PostList
  }
}
</script>