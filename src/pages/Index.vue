<template>
  <Layout :show-logo="false">
    <Box theme="dark">
      <Author :show-title="true" />
    </Box>

    <!-- List posts -->
    <div class="posts">
      <Box>
        <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node" />
      </Box>
    </div>
  </Layout>
</template>

<page-query>
query {
  posts: allPost(filter: { published: { eq: true }}) {
    edges {
      node {
        id
        title
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        cover_image (width: 770, height: 380, blur: 10)
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
import Author from "~/components/Author.vue";
import Box from "~/components/Box.vue";
import PostCard from "~/components/PostCard.vue";

export default {
  components: {
    Author,
    Box,
    PostCard
  },
  metaInfo: {
    title: "Hello, world!"
  }
};
</script>
