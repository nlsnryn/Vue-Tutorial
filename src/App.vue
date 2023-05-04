<template>
  <navbar
    :pages="pages"
    :page-index="pageIndex"
    :navbar-link="(index) => (pageIndex = index)"
  ></navbar>
  <page-viewer v-if="pages.length > 0" :page="pages[pageIndex]"></page-viewer>
  <create-page @page-created="pageCreated"></create-page>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import PageViewer from "./components/PageViewer.vue";
import CreatePage from "./components/CreatePage.vue";

export default {
  components: {
    Navbar,
    PageViewer,
    CreatePage,
  },
  created() {
    this.getPages();

    // For Global Event
    // this.$bus.$on("navbarLinkActivated", (index) => {
    //   this.pageIndex = index;
  },
  data() {
    return {
      pageIndex: 0,
      pages: [],
    };
  },
  methods: {
    async getPages() {
      let res = await fetch("pages.json");
      let data = await res.json();

      this.pages = data;
    },
    pageCreated(pageObj) {
      this.pages.push(pageObj);
    },
  },
};
</script>
