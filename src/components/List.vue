<template>
  <div>
    <h2>List</h2>

    <ul>
      <Item
        v-for="item in items"
        :key="item.id"
        :item="item"
        @remove-item="removeItem"
      />
    </ul>
  </div>
</template>

<script>
import Item from '@/components/Item.vue'

export default {
  name: 'List',
  components: {
    Item
  },
  props: {
    items: Array
  },
  methods: {
    removeItem (id) {
      this.$emit('remove-item', id)
    }
  }
}
</script>

<style lang="scss" scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>
