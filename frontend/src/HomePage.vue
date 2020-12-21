<template>
  <div id="home-page">
    <header class="hero-header">
      <img src="https://media.bizj.us/view/img/11379549/rothys*800xx662-374-0-56.jpg" alt="Hero" />
      <h2>{{ pageTitle }}</h2>
    </header>
    <p>
      {{ pageBody }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
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
@import "@/styles/_colors.scss";
@import "@/styles/_sizes.scss";
@import "@/styles/_typography.scss";

#home-page {
  font-size: $font-xxl;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  .hero-header {
    margin-bottom: $xxxl;
    text-align: center;
    img {
    }
    h2 {
      @include hero-font-1;
      margin-top: -$xl;
      color: $contrast-color-5;
      text-align: center;
      z-index: 10;
    }
  }
  p {
    max-width: 600px;
    line-height: 1.5;
  }
}
</style>
