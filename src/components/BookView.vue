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
  <PageGroup @choose="(page) => (currentId = page)" :pages="LU" type="lu" />
  <PageGroup @choose="(page) => (currentId = page)" :pages="unsatisfiedDependence" type="dependence" />
  <div style="border: sandybrown 1px solid; height: 400px; margin: 10px">
    <FileGroup :files="staticSampleTree" />
    {{ LU }}
    {{ current }}
    {{ unsatisfiedDependence }}
    {{ recommends }}
  </div>
  <PageGroup @choose="(page) => (currentId = page)" :pages="recommends" type="recommends" />
</template>

<script setup lang="ts">
import FileGroup from "./FileGroup.vue";
import PageGroup from "./PageGroup.vue";
import { ref, reactive, computed } from "vue";
const staticSampleTree = [
  { id: "grandparents", cxt: "They love you very much" },
  {
    id: "mom",
    cxt: "When she was young, she was even younger than you",
    dpd: ["grandparents"],
    rcm: ["daddy"],
  },
  { id: "daddy", cxt: "made a fortune", dpd: [], rcm: ["mom"] },
  {
    id: "me",
    cxt: "or *you*? whatever.",
    dpd: ["mom", "daddy"],
    rcm: ["sister", "wife", "cousin"],
  },
  {
    id: "sister",
    cxt: "your dear lovely sister",
    dpd: ["mom", "daddy"],
    rcm: ["me"],
  },
  {
    id: "nephew",
    cxt: "as clever as you at youth",
    dpd: ["sister"],
    rcm: ["niece"],
  },
  {
    id: "niece",
    cxt: "as clever as your sister at youth",
    dpd: ["sister"],
    rcm: ["nephew"],
  },
  { id: "wife", cxt: "_nice_", dpd: ["her_parents"] },
  { id: "her_parents", cxt: "have only one daughter", dpd: [] },
  { id: "son", cxt: "male", dpd: ["me", "wife"] },
  {
    id: "daughter",
    cxt: "female",
    dpd: ["me", "wife"],
    rcm: ["niece", "uncle's wife"],
  },
  {
    id: "grandson",
    cxt: "I don't know if it's okay for they to have a child,\n but it's not ok for me to type any more",
    dpd: ["daughter", "nephew2"],
  },
  {
    id: "granddaughter",
    cxt: "daughter of your daughter",
    dpd: ["daughter", ""], // maybe ex?
    rcm: ["nephew2"],
  },
  { id: "uncle", cxt: "brother of your mom", dpd: ["grandparents"] },
  {
    id: "uncle's wife",
    cxt: "~~Finally I decided not to assign a child to you and her~~",
    dpd: [],
  },
  {
    id: "cousin",
    cxt: "son of your mother's brother",
    dpd: ["uncle", "uncle's wife"],
  },
  {
    id: "nephew2",
    cxt: "son of son of your mother's brother",
    dpd: ["cousin"],
  },
  {
    id: "niece2",
    cxt: "not son of son of your mother's brother",
    dpd: ["cousin"],
  },
];
const LU = reactive(["grandparents", "daddy", "wife", "uncle's wife"]);
const currentId = ref("daughter");
const currentIndex = computed(() =>
  staticSampleTree.findIndex((i) => i.id === currentId.value),
);
function filterLu(array) {
  return array.filter((item) => LU.indexOf(item) === -1);
}
const current = computed(() => staticSampleTree[currentIndex.value]);
const unsatisfiedDependence = computed(() => filterLu(current.value.dpd || []));
const recommends = computed(() => filterLu(current.value.rcm || []));
// LU
// dpd
// now is daughter
// choices and their dependence graph
</script>

<style scoped></style>
<!-- should overflow x or something, and button thing -->
