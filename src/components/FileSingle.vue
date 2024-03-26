<template>
  <div class="editor">
    <textarea class="input" :value="input" @input="update"></textarea>
    <div class="output" v-html="output"></div>
  </div>
</template>

<script setup>
import { marked } from "marked";
import { debounce } from "lodash-es";
import { ref, computed } from "vue";
import { useLocalStorage } from "@vueuse/core";

const props = defineProps({
  filename: {
    type: String,
    required: true, // not working
  },
});

const input = useLocalStorage(props.filename, "# hello");
console.log(props.filename);

const output = computed(() => marked(input.value));

const update = debounce((e) => {
  input.value = e.target.value;
}, 100);
</script>

<style scoped>
.editor {
  display: flex;
}

.input,
.output {
  overflow: auto;
  width: 50%;
  box-sizing: border-box;
  padding: 0 20px;
}

.input {
  border: none;
  border-right: 1px solid #ccc;
  resize: none;
  outline: none;
  background-color: #f6f6f6;
  font-size: 14px;
  font-family: "Monaco", courier, monospace;
  padding: 20px;
}

code {
  color: #f66;
}
</style>
