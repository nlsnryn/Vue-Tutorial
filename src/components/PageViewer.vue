<template>
  <div class="container" id="content">
    <h1 class="emphasize">{{ page.pageTitle }}</h1>
    <p>{{ page.content }}</p>
  </div>
</template>

<script>
export default {
  props: ["page"],
};
</script>
