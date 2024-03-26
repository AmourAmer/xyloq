<!--
A simple markdown editor.
-->
<script setup>
import FileSingle from "./components/FileSingle.vue";
</script>

<template>
  <div style="
      border: aquamarine 1px solid;
      width: 400px;
      height: 1200px;
      margin: 10px;
    ">
    <FileSingle filename="demo" />
  </div>
</template>

<style>
body {
  margin: 0;
}
</style>
