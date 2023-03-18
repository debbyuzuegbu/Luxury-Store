<template>
  <section class="products">
    <h2>New Arrivals</h2>
    <p class="highlight">The latest products we have on sale</p>
    <div class="container">
      <div class="product__container" v-if="newArrivals">
        <product-card
          v-for="(product, id) in newArrivals"
          :key="id"
          :productId="product._id"
          :productName="product.title"
          :brand="product.brand"
          :price="product.price"
          :image_url="product.thumbnail"
          :in_stock="product.stock"
        />
      </div>
      <product-preloader type="inline" v-else>
        Loading products...
      </product-preloader>
    </div>
  </section>
</template>

<script>
import ProductCard from "@/components/home_components/cards/ProductCard.vue";
import ProductPreloader from "@/components/preloaders/ProductPreloader.vue";
export default {
  name: "NewArrivals",
  components: {
    ProductCard,
    ProductPreloader,
  },
  props: ["newArrivals"],
};
</script>
