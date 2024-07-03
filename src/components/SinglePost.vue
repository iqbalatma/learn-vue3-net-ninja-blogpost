<script>
export default {
  props: ['post'],
  setup() {

  }
}
</script>

<template>
  <div>
    <router-link :to="{name: 'detail', params: {id: post.id}}">
      <h2>{{ post.title }}</h2>
    </router-link>
    <p>{{post.body}}</p>
    <span v-for="tag in post.tags" :key="tag">#{{tag}}</span>
  </div>
</template>

<style scoped>

</style>