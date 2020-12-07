<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

    <HelloWorld
      msg="Welcome to Your Vue.js App"
    />

    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>

    <Loader v-if="loading" />

    <List
      v-else-if="filterItems.length"
      :items="filterItems"
      @remove-item="removeItem"
    />

    <p v-else>No items!</p>

    <ItemAdd
      @add-item="addItem"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import List from '@/components/List.vue'
import ItemAdd from '@/components/ItemAdd.vue'
import Loader from '@/components/Loader.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    List,
    ItemAdd,
    Loader
  },
  data () {
    return {
      items: [],
      loading: true,
      filter: 'all'
    }
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => response.json())
      .then(json => {
        this.items = json
        this.loading = false
      })
  },
  methods: {
    removeItem (id) {
      this.items = this.items.filter(elem => elem.id !== id)
    },
    addItem (item) {
      this.items.push(item)
    }
  },
  computed: {
    filterItems () {
      let filteredItems

      if (this.filter === 'all') {
        filteredItems = this.items
      }

      if (this.filter === 'completed') {
        filteredItems = this.items.filter(elem => elem.completed)
      }

      if (this.filter === 'not-completed') {
        filteredItems = this.items.filter(elem => !elem.completed)
      }

      return filteredItems
    }
  }
}
</script>
