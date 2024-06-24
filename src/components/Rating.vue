<script setup lang="ts">
const props = defineProps<{ rate: number }>();
const rate = props.rate < 0 || props.rate > 10 ? 0 : Math.ceil(props.rate * 10);
</script>

<template>
  <div
    class="rate"
    :style="`clip-path: polygon(0 50%, ${rate}% ${50 - rate / 2}%, ${rate}% ${50 + rate / 2}%, 0 50%)`"
  ></div>
</template>

<style scoped>
.rate {
  height: 10px;
  width: 266px;
  background: linear-gradient(
    90deg,
    rgba(195, 0, 0, 1) 0%,
    rgba(212, 230, 0, 1) 50%,
    rgba(0, 167, 6, 1) 100%
  );
  margin-top: 12px;
}
</style>
