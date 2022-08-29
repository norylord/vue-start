<template>
  <form @submit.prevent>
    <h3>Создание поста</h3>
    <my-input
        v-model="post.title"
        placeholder="Название"
        type="text"
    />
    <my-input
        v-model="post.body"
        placeholder="Описание"
        type="text"
    />
    <my-button
        class="button"
        style="align-self: flex-end"
        @click="createPost"
    >
      Создать
    </my-button>
  </form>
</template>

<script>

export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }
  },
}
</script>

<style scoped>

form {
  display: flex;
  justify-content: center;
  flex-direction: column;
  flex-grow: 1;
}


</style>