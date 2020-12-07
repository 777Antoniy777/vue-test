<template>
  <form @submit.prevent="handleFormSubmit">
    <input type="text" v-model="title" />
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  name: 'ItemAdd',
  props: {
    testFunc: Function
  },
  data () {
    return {
      title: ''
    }
  },
  methods: {
    handleFormSubmit () {
      if (this.title.trim()) {
        const newItem = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-item', newItem)
        this.title = ''
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  input {
    width: 400px;
  }
</style>
