<script setup>
import { ref } from "vue";
import TheTPOnboarding from "./components/TheTPOnboarding.vue";
import TheTPScene from "./components/TheTPScene.vue";

const loaded = ref(false);
</script>

<template>
  <TheTPOnboarding :loaded="loaded" />
  <TheTPScene @loaded="loaded = true"></TheTPScene>
</template>
