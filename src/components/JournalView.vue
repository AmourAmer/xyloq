<!-- xyloq, markdown viewer and journal maker from the wonderland -->
<!-- Copyright (C) 2024  AmourAmer -->
<!---->
<!-- This program is free software: you can redistribute it and/or modify -->
<!-- it under the terms of the GNU General Public License as published by -->
<!-- the Free Software Foundation, either version 3 of the License, or -->
<!-- (at your option) any later version. -->
<!---->
<!-- This program is distributed in the hope that it will be useful, -->
<!-- but WITHOUT ANY WARRANTY; without even the implied warranty of -->
<!-- MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the -->
<!-- GNU General Public License for more details. -->
<!---->
<!-- You should have received a copy of the GNU General Public License -->
<!-- along with this program.  If not, see <https://www.gnu.org/licenses/>. -->

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
