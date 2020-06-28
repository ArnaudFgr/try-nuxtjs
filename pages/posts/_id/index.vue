<template>
      <div>
        <h1>{{ post.title }}</h1>
        <p>{{ post.content }}</p>
      </div>
</template>

<script>
export default {
  data: () => ({
    post: {
      title: '',
      content: '',
      slug: ''
    }
  }),

  mounted() {
    // this.post = this.$store.state.posts.posts.find(post => post.slug === this.$route.params.id )
  },

  async asyncData({ store, route }){
    await store.dispatch('posts/all',[
      {
        title: 'Article 1',
        content: 'Content 1',
        slug: 'article-1',
      },
      {
        title: 'Article 2',
        content: 'Content 2',
        slug: 'article-2',
      }
    ])

    return {
      post: store.state.posts.posts.find(post => post.slug === route.params.id )
    }
  }
}
</script>

<style scoped>
</style>
