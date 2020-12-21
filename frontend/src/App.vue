<template>
  <div id="the-app">
    <h1>Sika Shoes</h1>
      <NavigationBar
          @navigate="navigate"
          :current-page='currentPage'/>
    <main>
      <component :is="currentPage" :pageData="currentPageData"/>
    </main>
  </div>
</template>

<script>
import NavigationBar from '@/components/NavigationBar.vue';
import HomePage from '@/HomePage.vue';
import ProductPage from '@/ProductPage.vue';
import AboutPage from '@/AboutPage.vue';

export default {
  name: 'App',
  data() {
    return {
      currentPage: 'home-page',
      products: [],
    };
  },
  components: {
    NavigationBar,
    HomePage,
    ProductPage,
    AboutPage,
  },
  methods: {
    navigate(newPage) {
      // console.log('got to parent navigate');
      this.currentPage = newPage;
    },
  },
  computed: {
    currentPageData() {
      const props = {
        'home-page': {
          pageBody: 'Shoes. Everybody wants them. The problem is, no one can figure out\n'
              + "where to buy them! That's why we created Sika Shoes. All you need to\n"
              + 'do is get the key from Gary, go down to the basement, unlock the door,\n'
              + "plug in the computer, and order some shoes. Let's get shoes on our feet!",
          pageTitle: 'Shoes just got cool again.',
        },
        'product-page': {
          products: this.products,
          pageTitle: 'Products',
        },
        'about-page': {
          pageBody: 'Sika Shoes is a small, fictional company that\'s commited to doing business\n'
              + 'the old-fashioned way: By making it all up.\n',
          pageTitle: 'About Us',
        },
      };

      return props[this.currentPage];
    },
  },
  created() {
    fetch('http://localhost:8091/products')
      .then((response) => response.json())
      .then((response) => {
        this.products = response.products;
      }).catch((error) => {
        this.error = error.message;
      });
  },
};
</script>

<style lang="scss">
</style>
