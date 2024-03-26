<template>
  <FileSingle v-for="file in files" :key="file" :filename="file" />
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import FileSingle from "./FileSingle.vue";

const props = defineProps({
  files: {
    type: Array<String>,
    required: true,
  },
});
</script>

<style scoped></style>
