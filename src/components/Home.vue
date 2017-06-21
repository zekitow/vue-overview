<template>
  <div class="hello">
    <h1>Home</h1>
    <p>{{ msg }}</p>

    <div class="posts">
      <div v-for="post in posts">
        <a v-on:click="remove(post)">Remove</a>
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
    remove: function(post) {
      this.posts.splice(this.posts.indexOf(post), 1);
    }
  },
  created: function() {
    this.$http.get('https://jsonplaceholder.typicode.com/posts')
        .then(function(response) {
          this.posts = response.data.splice(0, 5);
        });
  }
}
</script>

<style scoped>
h1 {
  font-weight: normal;
}
a {
  cursor: pointer;
  font-weight: bold;
  color: blue;
}
.posts {
  text-align: left;
}
</style>
