<template>
  <div class="navbar">
    <div @click="$router.push('/')">Vue 3</div>
    <div class="navbar__btns">
      <my-button @click="$router.push('/posts')">Posts</my-button>
      <my-button @click="$router.push('/about')">About</my-button>
    </div>
  </div>
</template>

<script>
export default {
  components: {}
}
</script>

<style scoped>
.navbar {
  height: 50px;
  background: #5051f9;
  box-shadow: 2px 2px 4px gray;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.navbar__btns {
  display: flex;
  justify-content: space-between;
}
</style>