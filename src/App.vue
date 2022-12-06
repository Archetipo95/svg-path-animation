<script setup lang="ts">
import Plane from './components/Plane.vue';
import { onMounted } from 'vue';

onMounted(() => {
  let svg = document.querySelectorAll('svg');

  let paths = document.querySelectorAll('path');

  fillSvgPaths();

  document.addEventListener('scroll', fillSvgPaths);

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
    <h1>eheh</h1>
  </section>

  <section>
    <h1>They go so fast</h1>
  </section>

  <section>
    <h1>EHEH</h1>
  </section>

  <Plane />
</template>

<style scoped></style>
