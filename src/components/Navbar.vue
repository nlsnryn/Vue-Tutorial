<template>
  <nav
    :class="['navbar', 'navbar-expand-lg', `navbar-${theme}`, `bg-${theme}`]"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Navbar</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul id="links" class="navbar-nav me-auto mb-2 mb-lg-0">
          <li v-for="(page, index) in pages" class="nav-item" :key="index">
            <a
              class="nav-link"
              :class="{ active: pageIndex == index }"
              aria-current="page"
              :href="page.link.url"
              :title="`The link is goes to ${page.link.navTitle} page`"
              @click.prevent="clickNavbar(index)"
              >{{ page.link.navTitle }}</a
            >
          </li>
        </ul>
        <div class="d-flex">
          <button class="btn btn-primary" @click.prevent="changeThemeColor()">
            Toggle Navbar
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  props: ["pages", "pageIndex", "clickNavbar"],

  data() {
    return {
      theme: "light",
    };
  },
  methods: {
    changeThemeColor() {
      let theme = "light";

      if (this.theme == "light") {
        theme = "dark";
      }

      this.theme = theme;
    },
  },
};
</script>
