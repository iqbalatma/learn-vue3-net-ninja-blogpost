<script>
import SinglePost from "@/components/SinglePost.vue";
export default {
  name: "PostList",
  components: {SinglePost},
  props: ["posts"]
}
</script>

<template>
  <SinglePost v-for="post in posts" :key="post.id" :post="post"></SinglePost>
</template>

<style scoped>

</style>