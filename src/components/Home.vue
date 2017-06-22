<template>
  <div class="hello">
    <h1>Home</h1>
    <p>{{ msg }}</p>

    <div class="posts">
      <div>
        <form v-on:submit="addPost">
          <input type="text" placeholder="title" v-model="newPost.title" /> <br>
          <textarea rows="5" placeholder="body" v-model="newPost.body"></textarea>
          <button>Save</button>
        </form>
      </div>
      <hr>
      <div v-for="post in posts">
        <div class="post">
          <a v-on:click="removePost(post)">Remove</a>
          <h2>{{ post.title }}</h2>
          <p>{{ post.body }}</p>
        </div>
      </div>
      <div class="message" v-if="posts.length == 0">
        <p>Sorry, no posts yet.</p>
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
      posts: [],
      newPost: {}
    }
  },
  methods: {
    addPost: function(e) {
      e.preventDefault();
      this.posts.push({
        title: this.newPost.title,
        body: this.newPost.body
      })
    },
    removePost: function(post) {
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
.message {
  color: #DDD;
  text-align: center;
}
.posts {
  text-align: left;
}

.posts .post {
  border: 1px solid #CCC;
  margin: 2em 0;
  padding: 1em;
}

input, textarea {
  width: 100%;
}
</style>
