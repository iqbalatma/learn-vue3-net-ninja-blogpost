<script>
import {ref} from "vue";
import {useRouter} from "vue-router"
export default {
  setup() {
    const title = ref('')
    const body = ref('')
    const tag = ref('')
    const tags = ref([])

    const router = useRouter()


    const addNewTag = () => {
      if (!tags.value.includes(tag.value)) {
        tag.value = tag.value.replace(/\s/, '')
        tags.value.push(tag.value)
      }
      tag.value = ''
    }

    const addNewPost = async () => {
      const post = {
        title: title.value,
        body: body.value,
        tags: tags.value
      }

      await fetch("http://localhost:3000/posts", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(post)
      })
    }
    return {
      title,
      body,
      tags,
      tag,
      addNewTag,
      addNewPost
    }
  }
}
</script>

<template>
  <div class="create">
    <form @submit.prevent="addNewPost">
      <label>Title:</label>
      <input type="text" v-model="title" required>
      <label>Content</label>
      <textarea required v-model="body"></textarea>
      <label>Tags</label>
      <input type="text" v-model="tag" @keydown.enter.prevent="addNewTag"/>
      <div v-for="tag in tags" :key="tag">#{{ tag }}</div>
      <button>Add Post</button>
    </form>
  </div>
</template>

<style scoped>

</style>