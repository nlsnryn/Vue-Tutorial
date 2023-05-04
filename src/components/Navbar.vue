<template>
  <nav
    :class="['navbar', 'navbar-expand-lg', `navbar-${theme}`, `bg-${theme}`]"
  >
    <div class="container">
      <a class="navbar-brand font-weight-bold" href="#">MyVue</a>
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
          <navbar-link
            v-for="(page, index) in publishedPages"
            class="nav-item"
            :key="index"
            :index="index"
            :page="page"
            :isActive="pageIndex == index"
            @navbar-link="navbarLink"
          ></navbar-link>
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
import NavbarLink from "./NavbarLink.vue";

export default {
  components: {
    NavbarLink,
  },
  computed: {
    publishedPages() {
      return this.pages.filter((p) => p.published);
    },
  },
  props: ["pages", "pageIndex", "navbarLink"],
  created() {
    this.getThemeSettings();
  },
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
      this.setThemeSettings();
    },
    setThemeSettings() {
      localStorage.setItem("theme", this.theme);
    },
    getThemeSettings() {
      let theme = localStorage.getItem("theme");

      if (theme) {
        this.theme = theme;
      }
    },
  },
};
</script>
