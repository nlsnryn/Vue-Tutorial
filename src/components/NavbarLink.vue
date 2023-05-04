<template>
  <li>
    <a
      class="nav-link"
      :class="activeClasses"
      aria-current="page"
      :href="page.link.url"
      :title="`The link is goes to ${page.link.title} page`"
      @click.prevent="$emit('navbarLink', index)"
      >{{ page.link.title }}</a
    >
  </li>
</template>

<script>
export default {
  props: ["page", "isActive", "index"],
  computed: {
    activeClasses() {
      return {
        active: this.isActive,
        emphasize: this.isActive,
      };
    },
  },
};
</script>

<style scoped>
.emphasize {
  text-decoration: underline !important;
}
</style>
