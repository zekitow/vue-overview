<template>
  <div class="hello">
    <h1>Home</h1>
    <p>{{ msg }}</p>

    <div class="posts">
      <div v-for="post in posts">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      msg: 'This is the home message',
      posts: []
    }
  },
  methods: {
  },
  created: function() {
    this.$http.get('https://jsonplaceholder.typicode.com/posts')
              .then(function(response) {
                this.posts = response.data;
              });
  }
}
</script>

<style scoped>
h1 {
  font-weight: normal;
}
.posts {
  text-align: left;
}
</style>
