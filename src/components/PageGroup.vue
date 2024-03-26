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
  <div>
    <button class="mx-2 px-2 pages" :class="typeClass" v-for="page in pages" :key="page" @click="$emit('choose', page)">
      {{ page }}
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

const props = defineProps({
  pages: {
    type: Array<String>,
    required: true,
  },
  type: String,
});

const emit = defineEmits(["choose"]);

const typeClass = computed(() => {
  if (props.type === "lu") return "bg-purple-500";
  else if (props.type === "dependence") return "bg-pink-400";
  else return "bg-red-400";
});
</script>

<style scoped></style>
<!-- should overflow x or something, and button thing -->
