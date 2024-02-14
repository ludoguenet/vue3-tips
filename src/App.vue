<script setup lang="ts">
import { ref } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

const modalRef = ref();
</script>

<template>
  <button @click="modalRef.openModal()">OpenFromTheOutside</button>

  <Suspense>
    <HelloWorld ref="modalRef" />

    <template #fallback>LOADING!!!!!</template>
  </Suspense>
</template>
