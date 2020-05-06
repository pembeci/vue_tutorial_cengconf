<template>
    <div class="blog-post" :class=" even ? 'even' : 'odd' ">
        <h3>{{ post.title }}</h3>
        <button>+</button><button>-</button>
        <div v-html="post.content"></div>
    </div>
</template>

<script>
export default {
  name: 'BlogPost',
  props: ['post', 'even']
}
</script>

<style scoped lang="scss">
  .blog-post {
      margin: 5px;
      border: 1px solid #ddd;
  }

  .even {
      background-color: lightgreen;
  }
  .odd {
      background-color: pink;
  }
</style>