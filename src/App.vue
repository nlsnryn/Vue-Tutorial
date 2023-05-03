<template>
  <navbar
    :pages="pages"
    :page-index="pageIndex"
    :click-navbar="(index) => (pageIndex = index)"
  ></navbar>
  <page-viewer :page="pages[pageIndex]"></page-viewer>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import PageViewer from "./components/PageViewer.vue";

export default {
  components: {
    Navbar,
    PageViewer,
  },
  data() {
    return {
      pageIndex: 0,
      pages: [
        {
          link: {
            navTitle: "Home",
            url: "index.html",
          },
          pageTitle: "Hello, Home",
          content: "Welcome to the world of Vue and Laravel",
        },
        {
          link: {
            navTitle: "About",
            url: "about.html",
          },
          pageTitle: "Hello, About",
          content: "Welcome to the world of Vue and Laravel",
        },
        {
          link: {
            navTitle: "Contact",
            url: "contact.html",
          },
          pageTitle: "Hello, Contact",
          content: "Welcome to the world of Vue and Laravels",
        },
      ],
    };
  },
};
</script>
