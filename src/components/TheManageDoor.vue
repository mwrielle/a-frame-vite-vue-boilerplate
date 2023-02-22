<script setup>
import "../aframe/clickable";
let doorState = false;
function doorAnimation() {
  if (doorState) {
    doorState = false;
    // document.querySelector("#cadre").removeAttribute("animation__open");
    document.querySelector("#cadre").dispatchEvent(new Event("close"));
  } else {
    doorState = true;
    // document.querySelector("#cadre").removeAttribute("animation__close");
    document.querySelector("#cadre").dispatchEvent(new Event("open"));
  }
}
</script>

<template>
  <a-entity
    id="cadre"
    position="0.5 0 0"
    animation__open="property: rotation; to: 0 90 0; loop: false; startEvents: open; dur: 1500;"
    animation__close="property: rotation; to: 0 0 0; loop: false; startEvents: close; dur: 1500;"
  >
    <a-entity
      clickable
      id="#door"
      gltf-model="#door"
      rotation="0 90 0"
      position="-0.5 0 0"
      scale="0.012 0.012 0.012"
      @click="doorAnimation()"
    >
    </a-entity>
  </a-entity>
</template>
