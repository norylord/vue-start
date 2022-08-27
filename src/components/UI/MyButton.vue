<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style scoped>

button {
  padding: 15px 30px;
  border-radius: 5px;
  margin: 10px;
  color: #fff;
  background-color: #5051f9;
  border: 0;
}
</style>