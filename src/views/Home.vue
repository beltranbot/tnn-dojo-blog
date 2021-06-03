<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList v-if="showPosts" :posts="posts"/>
    </div>
    <div v-else>Loadding...</div>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'
import PostList from "../components/PostList"
export default {
  name: 'Home',
  setup() {
    const showPosts = ref(true)
    const posts = ref([])
    const error = ref(null)

    const load = async () => {
      try {
        let data = await fetch("http://localhost:4000/posts")
        if (!data.ok) {
          throw Error("no data available")
        }
        posts.value = await data.json()
      } catch (err) {
        error.value = err.message
        console.log(error.value)
      }
    }

    load()

    return {
      posts,
      error,
      showPosts
    }
  },
  components: {
    PostList
  }
}
</script>