<script setup lang="ts">
import { onBeforeMount, ref } from "vue";
import { Product, Loader } from "components";
import { TLoadingState, TProduct } from "types.ts";

let products: TProduct[];
const loadingState = ref<TLoadingState>("loading");

onBeforeMount(async () => {
  const response = await fetch("https://fakestoreapi.com/products");
  products = await response.json();
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
