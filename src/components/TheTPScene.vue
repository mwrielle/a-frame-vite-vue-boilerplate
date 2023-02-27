<script setup>
import TheCameraRig from "./TheTPCameraRig.vue";
import TheTPGround from "./TheTPGround.vue";
import TheTPSwitch from "./TheTPSwitch.vue";
import { ref } from "vue";

const allAssetsLoaded = ref(false);
</script>

<template>
  <a-scene
    fog="type: linear; color: #ccc; near:2; far:10"
    background="color: #7a4d4a;"
    renderer="colorManagement: true;"
  >
    <a-entity environment="ground:'none';"></a-entity>

    <a-assets @loaded="allAssetsLoaded = true">
      <a-asset-item id="tree" src="/assets/oaktree.glb"></a-asset-item>
    </a-assets>
    <TheTPGround></TheTPGround>
    <TheTPSwitch></TheTPSwitch>
    <a-entity>
      <a-entity
        v-if="allAssetsLoaded"
        gltf-model="#tree"
        rotation="0 90 0"
        position="0 0 -2"
        scale="3 3 3"
      >
      </a-entity>
      <a-entity
        v-if="allAssetsLoaded"
        gltf-model="#tree"
        rotation="0 20 0"
        position="7 0 -7"
        scale="4 4 4"
      >
      </a-entity>
      <a-entity
        v-if="allAssetsLoaded"
        gltf-model="#tree"
        rotation="0 180 0"
        position="-4 0 -1"
        scale="5 5 5"
      >
      </a-entity>

      <a-entity
        v-if="allAssetsLoaded"
        gltf-model="#tree"
        rotation="0 110 0"
        position="0 0 3"
        scale="4 4 4"
      >
      </a-entity>

      <a-entity
        v-if="allAssetsLoaded"
        gltf-model="#tree"
        rotation="0 110 0"
        position="-3 0 7"
        scale="5 5 5"
      >
      </a-entity>

      <a-entity
        v-if="allAssetsLoaded"
        gltf-model="#tree"
        rotation="0 110 0"
        position="2 0 5"
        scale="8 8 8"
      >
      </a-entity>
    </a-entity>

    <TheCameraRig />
    <a-light type="ambient" color="#333"></a-light>
  </a-scene>
</template>
