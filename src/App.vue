<script setup lang="ts">
import { data as users } from "./data";
import { ref } from "vue";

const showUsers = ref(true);
const hoveredUserId = ref<number | null>(null);
</script>

<template>
  <div class="wrapper">
    <h1>ДЗ Шаблоны</h1>
    <button @click="showUsers = !showUsers">
      {{ showUsers ? "Скрыть список" : "Показать список" }}
    </button>

    <div v-if="showUsers">
      <div v-for="user in users" :key="user.id">
        <div
          @mouseover="hoveredUserId = user.id"
          @mouseleave="hoveredUserId = null"
        >
          <span class="name" :class="{ _hovered: hoveredUserId === user.id }">
            {{ user.name }}
          </span>
          <span v-show="user.id % 3" class="email">
            {{ " E-mail: " }}
            {{ user.email }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  margin: 40px;
  font-family: "Helvetica", sans-serif;
}

button {
  margin-bottom: 10px;
  padding: 5px 10px;
}

.name {
  font-size: 20px;
  line-height: 32px;
}

.email {
  color: grey;
}

._hovered {
  color: green;
}
</style>
