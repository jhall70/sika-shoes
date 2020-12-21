<template>
  <div id="about-page">
    <h2>{{pageTitle}}</h2>
    <p>
      {{ pageBody }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'AboutPage',
  props: {
    pageData: Object,
  },
  computed: {
    pageBody() {
      return this.pageData.pageBody;
    },
    pageTitle() {
      return this.pageData.pageTitle;
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/_sizes.scss";
@import "@/styles/_typography.scss";

#about-page {
  margin-top: 0;
  font-size: $font-xxxl;
}

h2 {
  @include heading-font-2;
  margin-bottom: $xxl;
  margin-top: 0;
}
</style>
