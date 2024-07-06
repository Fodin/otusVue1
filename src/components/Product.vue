<script setup lang="ts">
import { TProduct } from "types.ts";
import Image from "components/Image.vue";
import Rating from "components/Rating.vue";

defineProps<{ product: TProduct }>();
</script>

<template>
  <div class="wrapper">
    <Image class="image" :src="product.image" />
    <div class="title">{{ product.title }}</div>
    <div class="description">{{ product.description }}</div>
    <div class="price">${{ product.price }}</div>
    <Rating :rate="product.rating.rate" />
  </div>
</template>

<style scoped lang="scss">
.wrapper {
  position: relative;
  width: 300px;
  border: 1px solid #d6d6d6;
  border-radius: 8px;
  padding: 16px;
  background-color: white;
}

.title {
  font-size: 18px;
  line-height: 24px;
  text-align: left;
  width: 100%;
  font-weight: 600;
  color: #777;
  margin-top: 8px;
}

.description {
  margin-top: 4px;
  font-size: 14px;
  line-height: 22px;
}

.price {
  position: absolute;
  top: 10px;
  right: -8px;
  transform: rotate(-25deg);
  font-size: 38px;
  font-weight: bold;
  text-shadow:
    0 0 1px #000,
    1px 1px 10px #f8f4f4;
  color: #56ec34;
}
</style>
