<template>
  <div class="home">
    <div v-if="error">{{error}}</div>

    <div v-if="posts.length > 0">
      <PostList :posts="posts"></PostList>
    </div>
    <div v-else>
      <Spinner></Spinner>
    </div>
  </div>
</template>

<script>
import PostList from "@/components/PostList.vue";
import getPosts from "@/composeables/getPosts";
import Spinner from "@/components/Spinner.vue";
export default {
  name: 'HomeView',
  components: {
    Spinner,
    PostList
  },
  setup() {
    const {posts, error, load} = getPosts()

    load()
    return {
      error, posts
    }
  }
}
</script>
