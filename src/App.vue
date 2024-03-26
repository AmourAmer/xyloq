<!--
A simple markdown editor.
-->
<script setup>
import FileGroup from "./components/FileGroup.vue";
</script>

<template>
  <div style="
      border: aquamarine 1px solid;
      width: 400px;
      height: 1200px;
      margin: 10px;
    ">
    <FileGroup :files="['demo', 'demo2']" />
  </div>
</template>

<style>
body {
  margin: 0;
}
</style>
