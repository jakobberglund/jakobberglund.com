<template>
  <div class="post-card">
    <Box spaced>
      <div class="post-card__content">
        <h2 class="post-card__title" v-html="post.title" />
        <p class="post-card__description" v-html="post.description" />

        <PostMeta class="post-card__meta" :post="post" />
        <PostTags class="post-card__tags" :post="post" />

        <g-link class="post-card__link" :to="post.path">Link</g-link>
      </div>
    </Box>
  </div>
</template>

<script>
import Box from "~/components/Box";
import PostMeta from "~/components/PostMeta";
import PostTags from "~/components/PostTags";

export default {
  components: {
    Box,
    PostMeta,
    PostTags
  },
  props: ["post"]
};
</script>

<style lang="scss">
.post-card {
  position: relative;

  &:hover {
    box-shadow: 1px 10px 30px 0 rgba(0, 0, 0, 0.1);
  }

  &__title {
    margin-top: 0;
  }

  &__tags {
    z-index: 1;
    position: relative;
    display: inline-block;
  }

  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    overflow: hidden;
    text-indent: -9999px;
    z-index: 0;

    &:focus {
      outline: 1px solid black;
      opacity: 1;
    }
  }
}
</style>
