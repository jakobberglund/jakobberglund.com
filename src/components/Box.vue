<template>
  <section class="box" :class="cssModifiers">
    <slot />
  </section>
</template>

<script>
export default {
  props: {
    theme: {
      type: String,
      default: "light"
    },
    spaced: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    cssModifiers() {
      return {
        "box--light": this.theme === "light",
        "box--dark": this.theme === "dark",
        "box--spaced": this.spaced
      };
    }
  }
};
</script>

<style lang="scss">
.box {
  background-color: var(--bg-color);
  color: var(--body-color);

  &--light {
    --bg-color: var(--color1);
    --body-color: var(--color5);
    --title-color: var(--color5);
    --link-color: var(--color5);
  }

  &--dark {
    --bg-color: var(--color5);
    --body-color: var(--color1);
    --title-color: var(--color1);
    --link-color: var(--color1);
  }

  &--spaced {
    padding: calc(var(--space) / 2) var(--space);
  }
}
</style>
