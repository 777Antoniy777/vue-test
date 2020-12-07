<template>
  <li v-bind:class="{done: item.completed}">
    <input type="checkbox"
           @change="item.completed = !item.completed"
    >

    {{item.title | uppercase}}

    <button type="button"
            @click="$emit('remove-item', item.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  name: 'Item',
  props: {
    item: Object
  },
  filters: {
    uppercase (value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style lang="scss" scoped>
  li {
    display: flex;
    align-items: center;
    min-height: 50px;
    margin-bottom: 10px;
    border: 1px solid gray;
  }

  button {
    margin-left: auto;
  }

  .done {
    border-color: green;
    text-decoration: line-through;
  }
</style>
