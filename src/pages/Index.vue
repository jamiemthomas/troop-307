<template>
  <Layout>
    <!-- Author intro -->
    <Hero :show-title="true" />

    <!-- List posts -->
    <section class="section posts">
      <div class="container">
        <PostCard
          v-for="edge in $page.posts.edges"
          :key="edge.node.id"
          :post="edge.node"
        />
      </div>
    </section>
  </Layout>
</template>

<page-query>
  query {
    posts: allPost(sortBy: "date") {
      edges {
        node {
          id
          title
          date(format: "D. MMMM YYYY")
          timeToRead
          description
          cover_image(width: 770, height: 380, blur: 10)
          path
          tags {
            id
            title
            path
          }
        }
      }
    }
  }
</page-query>

<script>
import Hero from '~/components/Hero.vue';
import PostCard from '~/components/PostCard.vue';

export default {
  components: {
    Hero,
    PostCard,
  },
  metaInfo: {
    title: 'Home',
  },
};
</script>
