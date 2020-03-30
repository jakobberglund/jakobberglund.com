<template>
  <div class="author" :class="cssModifiers">
    <h1 v-if="showTitle" class="author__site-title">{{ $static.metadata.siteName }}</h1>
    <p class="author__intro">
      Independent front-end web developer for hire.
      <br />Musician in A Swarm of the Sun.
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
  props: {
    showTitle: {
      type: Boolean,
      default: false
    },
    center: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    cssModifiers() {
      return {
        "author--center": this.center
      };
    }
  }
};
</script>

<style lang="scss">
.author {
  padding: calc(var(--space) / 2) var(--space);

  &__intro {
    opacity: 0.8;
  }

  &__site-title {
    font-size: var(--font-size--jumbo);
  }

  &__links {
    margin-top: -0.5em;

    a {
      margin: 0 0.5em 0 0;

      .author--center & {
        margin: 0 0.25em;
      }
    }
  }

  &--center {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
}
</style>
