<template>
  <main-header />
  <section class="hero__section">
    <div class="container">
      <div class="hero__text">
        <h4>Shop with us</h4>
        <h1>Best value deals</h1>
        <h2>On all products in the store</h2>
        <p>Save more with coupons & get up to 50% off!</p>
        <router-link to="/shop">
          <action-button btnvalue="Start Shopping" />
        </router-link>
      </div>
    </div>
  </section>
  <service-section />
  <section class="feature__section">
    <div class="container">
      <featured-products :featuredProducts="featuredProducts" />
    </div>
  </section>

  <banner-section />
  <new-arrivals :newArrivals="newArrivals" />
  <main-footer />
</template>

<script>
import ServiceSection from "@/components/home_components/ServiceSection.vue";
import BannerSection from "@/components/home_components/BannerSection.vue";
import NewArrivals from "@/components/home_components/products/NewArrivals.vue";
import FeaturedProducts from "@/components/home_components/products/FeaturedProducts.vue";
import ActionButton from "@/components/ActionButton.vue";
import MainHeader from "@/components/MainHeader.vue";
import MainFooter from "@/components/MainFooter.vue";

import axios from "axios";
import { mapActions } from "vuex";

export default {
  name: "HomeView",
  data() {
    return {
      products: [],
    };
  },
  methods: {
    ...mapActions(["set_products"]),
  },
  components: {
    ServiceSection,
    BannerSection,
    NewArrivals,
    FeaturedProducts,
    ActionButton,
    MainHeader,
    MainFooter,
  },
  computed: {
    isAuth() {
      return this.$store.getters.userIsAuthenticated;
    },
    getProducts() {
      return this.$store.getters.getProduct;
    },
    featuredProducts() {
      return this.products.slice(1, 5);
    },
    newArrivals() {
      return this.products.slice(5, 9);
    },
  },
  async created() {
    let res1 = await axios.get("https://gorana.onrender.com/products");
    this.products = res1.data.results.map((product) => {
      product.images[0] = product.images[0].replace("http", "https");
      console.log(product);
      return product;
    });
    this.set_products(this.products);
  },
};
</script>

<style scoped>
/* Hero Section */
.hero__section {
  display: flex;
  align-items: center;
  justify-content: center;
  height: calc(100vh - 65px);
  background-image: url("https://i.dummyjson.com/data/products/1/3.jpg");
  background-position: 60% 30%;
  background-size: cover;
}

.hero__text {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-direction: column;
}

.hero__text h4 {
  padding-bottom: 1rem;
}

.hero__text h1 {
  color: var(--dim-blue);
}

.hero__text p {
  margin-bottom: 1rem;
}

@media (min-width: 2000px) {
  .hero__section {
    background-position: 70% 12%;
    background-size: contain;
    background-repeat: no-repeat;
    background-color: #bfc3d6;
    height: 50vh;
  }
}

@media (min-width: 3000px) {
  .hero__section {
    background-position: 60% 30%;
    /* background-size: cover; */
  }
}
</style>
