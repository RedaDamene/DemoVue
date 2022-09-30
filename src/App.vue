<script>
import PostsList from './components/PostsList.vue';
import Post from './components/Post.vue';
import Comments from './components/Comments.vue';

const API_URL = `https://jsonplaceholder.typicode.com/`

export default {
  data() {
    return {
      res: null
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((response) => response.json())
      .then(posts => this.res = posts);
  },
  components: {
    PostsList,
    Post,
    Comments
  }
}

</script>

<template>
  <Post />
  <PostsList />
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
