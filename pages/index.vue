<template>
  <div>
    <main>
      <b-container>
        <b-row>
          <b-col>
            <ul>
              <li v-for="(post, index) in posts" :key="index"><nuxt-link :to="{ name: 'posts-id', params: { id: post.slug }}">{{ post.title }}</nuxt-link></li>
            </ul>
          </b-col>
        </b-row>
      </b-container>
    </main>
  </div>
</template>

<script>

export default {
  data: () => ({
    posts: [],
  }),

  async asyncData({ store }) {
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
      posts: store.state.posts.posts
    }
  }
}
</script>

<style scoped>
</style>
