<template>
  <Page>
    <div class="has-text-centered">
      <h1 class="title is-1">
        {{ $page.post.title }}
      </h1>
      <PostMeta
        :post="$page.post"
        class="subtitle is-size-6"
      />
    </div>

    <div class="post content section">
      <figure
        v-if="$page.post.cover_image"
        class="image is-16by9"
      >
        <g-image
          :src="$page.post.cover_image"
          alt="Cover image"
          style="object-fit:contain;"
        />
      </figure>

      <p v-html="$page.post.content" />

      <footer>
        <PostTags :post="$page.post" />
      </footer>
    </div>

    <div class="post-comments">
      <!-- Add comment widgets here -->
    </div>
  </Page>
</template>

<script>
import PostMeta from '~/components/PostMeta';
import PostTags from '~/components/PostTags';

export default {
  components: {
    PostMeta,
    PostTags,
  },
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: 'description',
          content: this.$page.post.description,
        },
      ],
    };
  },
};
</script>

<page-query>
  query Post($id: ID!) {
    post: post(id: $id) {
      title
      path
      date(format: "D. MMMM YYYY")
      timeToRead
      tags {
        id
        title
        path
      }
      description
      content
      cover_image(width: 860, blur: 10)
    }
  }
</page-query>
