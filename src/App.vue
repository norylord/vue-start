<template>
  <div class="app">

    <h1>Страница с постами</h1>
    <my-input
        v-model="searchQuery"
        placeholder="Поиск..."
    />
    <div class="app_btns">
      <my-button
          @click="showDialog"
      >
        Создать пост
      </my-button>
      <my-select
          v-model="selectedSort"
          :options="sortOptions"
      />
    </div>

    <my-dialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </my-dialog>

    <post-list
        v-if="!isPostLoading"
        :posts="sortedAndSearchedPosts"
        @remove="removePost"
    />
    <h3 v-else>
      Идет загрузка...
    </h3>
  </div>
</template>

<script>

import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyDialog from "@/components/UI/MyDialog";
import MyButton from "@/components/UI/MyButton";
import axios from "axios";
import MySelect from "@/components/UI/MySelect";
import MyInput from "@/components/UI/MyInput";

export default {
  components: {
    MyInput,
    MyButton,
    MyDialog,
    MySelect,
    PostList,
    PostForm
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostLoading: false,
      selectedSort: '',
      searchQuery: '',
      sortOptions: [
        {value: 'title', name: 'По наименованию'},
        {value: 'body', name: 'По описанию'},
      ]
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = response.data
      } catch {
        alert('Error')
      } finally {
        console.log('1231')
        this.isPostLoading = false
      }
    }
  },
  mounted() {
    this.fetchPosts()
  },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((a, b) => a[this.selectedSort]?.localeCompare(b[this.selectedSort]))
    },
    sortedAndSearchedPosts() {
      return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Arial", sans-serif;
}

.app {
  padding: 20px;

}

.app_btns {
  display: flex;
  justify-content: space-between;
}

</style>