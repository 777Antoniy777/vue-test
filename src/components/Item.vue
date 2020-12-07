<template>
  <li v-bind:class="{done: item.status}">
    <input type="checkbox"
           v-on:change="item.status = !item.status"
    >

    {{item.content}}

    <button type="button"
            v-on:click="$emit('remove-item', item.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  name: 'Item',
  props: {
    item: Object
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
