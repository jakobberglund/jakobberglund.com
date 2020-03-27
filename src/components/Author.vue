<template>
  <div class="author">
    <g-image
      alt="A picture of me"
      class="author__image"
      src="~/assets/images/me.jpg"
      width="180"
      height="180"
      blur="5"
    />

    <h1 v-if="showTitle" class="author__site-title">{{ $static.metadata.siteName }}</h1>

    <p class="author__intro">
      Independent front-end web developer for hire.
      <br />Musician in
      <br />Photographer and videographer.
    </p>

    <p class="author__links">
      <a href="mailto:contact@jakobberglund.com">Email</a>
      <a href="//twitter.com/jakobberglund">Twitter</a>
      <a href="//www.linkedin.com/in/jakobberglund">Linkedin</a>
      <a href="//github.com/jakobberglund">GitHub</a>
      <a href="//www.aswarmofthesun.com">Music</a>
    </p>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
export default {
  props: ["showTitle"]
};
</script>

<style lang="scss">
.author {
  margin: 0 auto;
  max-width: 500px;
  text-align: center;
  padding: calc(var(--space) / 2) 0;

  &__image {
    border-radius: 100%;
    width: 90px;
    height: 90px;
    margin-bottom: 1em;
  }

  &__intro {
    opacity: 0.8;
  }

  &__site-title {
    font-size: 1.5em;
  }

  &__links {
    margin-top: -0.5em;
    a {
      margin: 0 0.5em;
    }
  }
}
</style>
