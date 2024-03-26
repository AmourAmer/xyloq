<script setup>
import JournalView from "./components/JournalView.vue";
import BookView from "./components/BookView.vue";
import { ref } from "vue";
const license = ref(false);
const view = ref("journal");
function toggleView() {
  if (view.value === "journal") view.value = "book";
  else view.value = "journal";
}
</script>

<template>
  <header>
    <button class="bg-gray-500 mx-2 px-2" @click="toggleView">
      Current View: {{ view }}
    </button>
    <button class="bg-gray-500 mx-2 px-2" @click="license = !license">
      About -> Lisence
    </button>
  </header>
  <JournalView v-if="view === 'journal'" />
  <BookView v-else />
  <object data="../LICENSE" style="width: 100%" v-if="license"></object>
</template>

<style>
body {
  margin: 0;
}
</style>
