<template>
  <Layout>
    <g-image
      alt="Cover image"
      v-if="$page.post.cover_image"
      :src="$page.post.cover_image"
      class="post-image"
    />
    <Box>
      <div class="post-title">
        <h1 class="post-title__text">{{ $page.post.title }}</h1>

        <PostMeta :post="$page.post" />
      </div>

      <div class="post">
        <div class="post__header"></div>

        <div class="post__content" v-html="$page.post.content" />

        <div class="post__footer">
          <PostTags :post="$page.post" />
        </div>
      </div>
    </Box>

    <div class="post-comments">
      <!-- Add comment widgets here -->
    </div>

    <Box theme="dark">
      <Author class="post-author" center />
    </Box>
  </Layout>
</template>

<script>
import Box from "~/components/Box";
import PostMeta from "~/components/PostMeta";
import PostTags from "~/components/PostTags";
import Author from "~/components/Author.vue";

export default {
  components: {
    Author,
    Box,
    PostMeta,
    PostTags
  },
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: "description",
          content: this.$page.post.description
        }
      ]
    };
  }
};
</script>

<page-query>
query Post ($id: ID!) {
  post: post (id: $id) {
    title
    path
    date (format: "MMMM D, YYYY")
    timeToRead
    tags {
      id
      title
      path
    }
    description
    content
    cover_image (height: 700, blur: 10)
  }
}
</page-query>

<style lang="scss">
.post-image {
  width: 100%;
}

.post-title {
  padding: calc(var(--space) / 2) 0 calc(var(--space) / 2);
  text-align: center;
}

.post {
  display: flex;
  flex-direction: column;
  align-items: center;

  &__header {
    width: calc(100% + var(--space) * 2);
    margin-left: calc(var(--space) * -1);
    margin-top: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    img {
      width: 100%;
    }

    &:empty {
      display: none;
    }
  }

  &__content {
    h2:first-child {
      margin-top: 0;
    }

    p {
      max-width: 700px;

      &:first-of-type {
        font-size: 1.2em;
        color: var(--title-color);
      }
    }

    img {
      width: calc(100% + var(--space) * 2);
      margin-left: calc(var(--space) * -1);
      display: block;
      max-width: none;
    }
  }
}

.post-comments {
  padding: calc(var(--space) / 2);

  &:empty {
    display: none;
  }
}

.post-author {
  margin-top: calc(var(--space) / 2);
}
</style>
