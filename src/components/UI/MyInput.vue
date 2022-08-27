<template>
  <input :value="modelValue" class="input" type="text" @input="updateInput">
</template>

<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>
.input {
  width: 100%;
  padding: 10px 15px;
  margin: 10px 5px;
  outline: none;
  border: 0;
  border-bottom: 2px solid #5051f9;
}

</style>