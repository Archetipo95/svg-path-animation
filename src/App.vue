<script setup lang="ts">
import DickButt from "./components/DickButt.vue";
import { onMounted } from "vue";

onMounted(() => {
  let paths = document.querySelectorAll("path");

  fillSvgPaths();

  document.addEventListener("scroll", fillSvgPaths);

  function fillSvgPaths() {
    let scrollPercentage =
      (document.documentElement.scrollTop + document.body.scrollTop) /
      (document.documentElement.scrollHeight -
        document.documentElement.clientHeight);

    for (var i = 0; i < paths.length; i++) {
      let path = paths[i];

      let pathLength = path.getTotalLength();

      path.style.strokeDasharray = pathLength;
      path.style.strokeDashoffset = pathLength;

      let drawLength = pathLength * scrollPercentage;

      path.style.strokeDashoffset = pathLength - drawLength;
    }
  }
});
</script>

<template>
  <section>
    <h1>Plz scroll</h1>
  </section>

  <section>
    <h1>Faster!</h1>
  </section>

  <section>
    <h1>EHEH</h1>
  </section>

  <DickButt />
</template>

<style scoped></style>
