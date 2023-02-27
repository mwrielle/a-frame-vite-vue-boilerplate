<script setup>
import "../aframe/clickable";

let ligthStatus = false;

function lightSwitch() {
  if (ligthStatus) {
    ligthStatus = false;
    document.querySelector("a-light").setAttribute("color", "#fff");
  } else {
    ligthStatus = true;
    document.querySelector("a-light").setAttribute("color", "#333");
  }
}
</script>
<template>
  <a-box
    clickable
    position="2.9 1.3 5"
    rotation="0 90 0"
    color="lightgrey"
    width="0.1"
    height="0.1"
    depth="0.05"
    @click="lightSwitch()"
  ></a-box>
  <a-entity
    position="2.90 1.4 4.75"
    rotation="0 90 0"
    text="value: Light switch, 
        press me;"
  ></a-entity>
</template>
