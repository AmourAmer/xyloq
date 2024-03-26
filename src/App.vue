<script setup>
import JournalView from "./components/JournalView.vue";
import { ref } from "vue";
const license = ref(false);
</script>

<template>
  <header>
    <button @click="license = !license">About -> Lisence</button>
  </header>
  <JournalView />
  <object data="../LICENSE" style="width: 100%" v-if="license"></object>
</template>

<style>
body {
  margin: 0;
}
</style>
