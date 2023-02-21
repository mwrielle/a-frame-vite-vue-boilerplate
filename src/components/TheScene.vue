<!-- <script setup></script>

<template>
  <a-scene background="color: black;" renderer="colorManagement: true;">
    <a-box position="0 1 -3" color="purple"></a-box>
    <a-entity
      scale="3 3 3"
      rotation="0 90 0"
      gltf-model="url(assets/monstera.glb)"
    ></a-entity>
  </a-scene>
</template> -->

<script setup>
import { ref } from "vue";
import { randomHsl } from "../utils/color.js";

import BoxColorChanging from "./BoxColorChanging.vue";
import TheCameraRig from "./TheCameraRig.vue";
import TheNavMesh from "./TheNavMesh.vue";

import "../aframe/life-like-automaton";

defineProps({
  scale: Number,
  overlaySelector: String,
});

const colorBoxLeft = ref(randomHsl());
const colorBoxRight = ref(randomHsl());
const allAssetsLoaded = ref(false);
</script>

<template>
  <a-scene
    background="color: #eee;"
    renderer="colorManagement: true;"
    :webxr="`
      requiredFeatures: local-floor;
      referenceSpaceType: local-floor;
      optionalFeatures: dom-overlay;
      overlayElement: ${overlaySelector};
    `"
  >
    <a-assets @loaded="allAssetsLoaded = true">
      <a-asset-item id="monstera" src="assets/monstera.glb"></a-asset-item>
      <a-asset-item
        id="potted-plant"
        src="assets/potted_plant.glb"
      ></a-asset-item>
      <a-asset-item id="hoya" src="assets/hoya_plant.glb"></a-asset-item>
      <a-asset-item id="caisse" src="assets/caisse.glb"></a-asset-item>
      <a-asset-item id="etagere" src="assets/etagere.glb"></a-asset-item>
      <a-asset-item id="coquillage" src="assets/sea_shell.glb"></a-asset-item>
    </a-assets>

    <a-box
      class="wallpaper-front"
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="0"
      height="3"
      width="8"
      position="0 1.4 -13"
    ></a-box>

    <a-box
      class="wallpaper-back"
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="0"
      height="3"
      width="8"
      position="0 1.4 3"
    ></a-box>

    <a-box
      class="wallpaper-floor"
      material="src:../../public/assets/texture-background.jpg"
      rotation="-90 0 0"
      color=""
      height="16.5"
      width="8"
      position="0 -0.4 -4.75"
    ></a-box>

    <a-box
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="16"
      height="3"
      width="0"
      position="-4 1.4 -5"
    ></a-box>

    <a-box
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="16"
      height="3"
      width="0"
      position="4 1.4 -5"
    ></a-box>

    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#monstera"
      rotation="0 90 0"
      position="1 0.6 -1"
      scale="1 1 1"
    >
    </a-entity>

    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#potted-plant"
      rotation="0 90 0"
      position="0 1.26 -1.31"
      scale="0.05 0.05 0.05"
    >
    </a-entity>

    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#hoya"
      rotation="0 90 0"
      position="0 0.74 -1.33"
      scale="3 3 3"
    >
    </a-entity>
    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#etagere"
      rotation="0 90 0"
      position="0 1.09 -1.4"
      scale="3 3 3"
    >
    </a-entity>
    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#caisse"
      rotation="0 180 0"
      position="0 0 -1.7"
      scale="0.035 0.035 0.035"
    >
    </a-entity>

    <a-entity
      v-if="allAssetsLoaded"
      gltf-model="#coquillage"
      rotation="0 90 0"
      position="0.1 0.99 -1.4"
      scale="0.6 0.6 0.6"
    >
    </a-entity>

    <TheNavMesh />

    <TheCameraRig />
  </a-scene>
</template>
