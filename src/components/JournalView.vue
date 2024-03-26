<template>
  <div style="
      border: aquamarine 1px solid;
      width: 400px;
      height: 400px;
      margin: 10px;
    ">
    <FileGroup :files="['demo', 'demo2']" />
  </div>
</template>

<script setup lang="ts">
import FileGroup from "./FileGroup.vue";
import { ref, computed } from "vue";
</script>

<style scoped></style>
<!-- should overflow x or something, and button thing -->
