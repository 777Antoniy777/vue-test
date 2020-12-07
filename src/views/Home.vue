<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

    <HelloWorld
      msg="Welcome to Your Vue.js App"
    />

    <List
      v-bind:items="items"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import List from '@/components/List.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    List
  },
  data () {
    return {
      items: [
        {
          id: 1,
          content: 'Item 1',
          status: false
        },
        {
          id: 2,
          content: 'Item 2',
          status: false
        },
        {
          id: 3,
          content: 'Item 3',
          status: false
        }
      ]
    }
  }
}
</script>
