<template>
  <div>
    <button v-for="file in files" :key="file" @click="setFile(file)">
      {{ file }}
    </button>
    <FileSingle v-for="file in uniq(files)" :key="file" v-show="file === currentFilename" :filename="file" />
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import { uniq } from "lodash-es";
import FileSingle from "./FileSingle.vue";

const props = defineProps({
  files: {
    type: Array<String>,
    required: true,
  },
});

const currentFilename = ref(props.files[0]); // whatif empty? should be some greeting

function setFile(file) {
  currentFilename.value = file;
}
</script>

<style scoped></style>
<!-- should overflow x or something, and button thing -->
