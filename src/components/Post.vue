<template>
  <div v-for="post in posts" v-bind:key="post.key" class="post">
    <div><strong>Название:</strong> {{ post.title }}</div>
    <div><strong>Описание:</strong> {{ post.body }}</div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>

</style>