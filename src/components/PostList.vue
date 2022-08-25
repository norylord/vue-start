<template>
  <div v-for="post in posts" v-bind:key="post.key" class="post">
    <div><strong>Название:</strong> {{ post.title }}</div>
    <div><strong>Описание:</strong> {{ post.body }}</div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>

.post {
  padding: 15px;
  border: 2px solid #5051f9;
  margin: 15px 10px;
}
</style>