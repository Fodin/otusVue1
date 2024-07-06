<script setup lang="ts">
import { ref, watchEffect } from "vue";
import { Product, Loader } from "components";
import { TLoadingState, TProduct } from "types.ts";

const products = ref<TProduct[]>();
const loadingState = ref<TLoadingState>("loading");

watchEffect(async () => {
  const response = await fetch("https://fakestoreapi.com/products");
  products.value = await response.json();
  loadingState.value = "success";
});
</script>

<template>
  <Loader v-if="loadingState === 'loading'" />
  <main v-else class="wrap">
    <Product v-for="product in products" :key="product.id" :product="product" />
  </main>
</template>

<style scoped>
.wrap {
  background-color: #edfdf6;
  margin: 0 auto;
  padding: 16px 0;
  max-width: 1280px;
  display: flex;
  flex-wrap: wrap;
  align-items: start;
  gap: 16px;

  justify-content: center;
}
</style>
