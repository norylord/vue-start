<template>
  <form @submit.prevent>
    <h3>Создание поста</h3>
    <input
        v-model="post.title"
        class="input"
        placeholder="Название"
        type="text"
    >
    <input
        v-model="post.body"
        class="input"
        placeholder="Описание"
        type="text"
    >
    <button
        class="button"
        @click="createPost"
    >
      Создать
    </button>
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
  }
}
</script>

<style scoped>

form {
  display: flex;
  justify-content: center;
  flex-direction: column;
  flex-grow: 1;
}


.input {
  width: 100%;
  padding: 10px 15px;
  margin: 10px 5px;
  outline: none;
  border: 0;
  border-bottom: 2px solid #5051f9;
}

button {
  padding: 15px 30px;
  border-radius: 5px;
  margin: 10px;
  color: #fff;
  background-color: #5051f9;
  border: 0;
  align-self: flex-end;
}
</style>