<template>
  <div class="product-list">
    <ProductCard
      v-for="product in products"
      :key="product.name"
      :name="product.name"
      :description="product.name"
      :price="product.price"
      :image="product.image"
    />
  </div>
</template>

<script>
import ProductCard from "./ProductCard.vue";
export default {
  name: "ProductList",
  components: { ProductCard },
  props: {
    products: {
      type: Array,
      required: true, // Список товарів передається з батьківського компонента
    },
  },
};
</script>

<style scoped>
.product-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}
</style> 