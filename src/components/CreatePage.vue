<template>
  <form action="" class="container mb-3 mt-3">
    <div class="row">
      <div class="cold-md-8">
        <div class="mb-3">
          <label for="" class="form-label">Page Title</label>
          <input type="text" class="form-control" v-model="pageTitle" />
        </div>
        <div class="mb-3">
          <label for="" class="form-label">Content</label>
          <textarea
            type="text"
            class="form-control"
            rows="5"
            v-model="content"
          ></textarea>
        </div>
      </div>
      <div class="col">
        <div class="mb-3">
          <label for="" class="form-label">Link Text</label>
          <input type="text" class="form-control" v-model="linkText" />
        </div>
        <div class="mb-3">
          <label for="" class="form-label">Link URL</label>
          <input type="text" class="form-control" v-model="linkURL" />
        </div>
        <div class="mb-3 row">
          <div class="form-check ml-3">
            <input
              type="checkbox"
              class="form-check-input"
              v-model="published"
            />
            <label for="gridCheck1" class="form-check-label">Published</label>
          </div>
        </div>
        <div class="mb-3">
          <button
            class="btn btn-primary"
            :disabled="isFormInvalid"
            @click.prevent="submitForm"
          >
            Create Page
          </button>
        </div>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  emits: {
    pageCreated(pageTitle, content, link) {
      if (!pageTitle) {
        return false;
      }

      if (!content) {
        return false;
      }

      if (!link || !link.title || !link.url) {
        return false;
      }
    },
  },
  computed: {
    isFormInvalid() {
      return (
        !this.pageTitle || !this.content || !this.linkText || !this.linkURL
      );
    },
  },
  data() {
    return {
      pageTitle: "",
      content: "",
      linkText: "",
      linkURL: "",
      published: true,
    };
  },
  methods: {
    submitForm() {
      if (!this.pageTitle || !this.content || !this.linkText || !this.linkURL) {
        alert("Please fill out the form");
        return;
      }

      this.$emit("pageCreated", {
        pageTitle: this.pageTitle,
        content: this.content,
        link: { title: this.linkText, url: this.linkURL },
        published: this.published,
      });

      this.pageTitle = "";
      this.content = "";
      this.linkText = "";
      this.linkURL = "";
      this.published = true;
    },
  },
  watch: {
    pageTitle(newTitle, oldTitle) {
      if (this.linkText === oldTitle) {
        this.linkText = newTitle;
      }
    },
    // linkText(newTitle) {
    //   if (this.linkText === "") {
    //     this.linkURL = "";
    //   } else {
    //     this.linkURL = newTitle.toLowerCase() + "." + "html";
    //   }
    // },
  },
};
</script>
