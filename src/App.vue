<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <button @click="fetchPosts">
    get posts
  </button>
  <div v-for="post in posts" :key="post.data">
    <div class="post">
      {{ post.name }}
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      posts: []
    }
  },
  methods: {
    async fetchPosts() {
      try {
        const response = await axios.get('https://flems.github.io/test/api/news')
        this.posts = response.data.items
      } catch (e) {
        alert('Error')
      }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.post {
  border: 1px solid black;
}
</style>
