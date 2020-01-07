<template>
  <div class="hello">
    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.body }}</li>
    </ul>
  </div>
</template>

<script>
import Api from '../apis/api.js';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      posts: null,
    }
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    getPosts () {
      Api.getPosts()
        .then(response => {
          this.posts = response.data;

        })
        .catch(error => {
          console.error(error);
        })
    }
  }
}
</script>
