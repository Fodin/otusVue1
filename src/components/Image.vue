<script setup lang="ts">
defineProps<{ src: string }>();
</script>

<template>
  <div class="container">
    <img :src="src" alt="" class="image" />
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100%;
  height: 250px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.image {
  max-width: 100%;
  max-height: 250px;
}
</style>
