<script setup>
import { ref } from "vue";
import { randomHsl } from "../utils/color.js";
import TheCameraRig from "./TheCameraRig.vue";
import TheNavMesh from "./TheNavMesh.vue";
import TheManageDoor from "./TheManageDoor.vue";
import "../aframe/clickable";

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
      <a-asset-item id="door" src="assets/door.glb"></a-asset-item>
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
      v-if="allAssetsLoaded"
      class="wallpaper-front-1"
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="0"
      height="0.33"
      width="8"
      position="0 2.75 -13"
    ></a-box>
    <a-box
      v-if="allAssetsLoaded"
      class="wallpaper-front-2"
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="0"
      height="3"
      width="2.95"
      position="-2.55 1.4 -13"
    ></a-box>

    <a-box
      v-if="allAssetsLoaded"
      class="wallpaper-front-3"
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="0"
      height="3"
      width="4"
      position="2 1.4 -13"
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
      v-if="allAssetsLoaded"
      class="wallpaper-floor"
      material="src:../../public/assets/texture-background.jpg"
      rotation="-90 0 0"
      color=""
      height="16.5"
      width="8"
      position="0 -0.4 -4.75"
    ></a-box>

    <a-box
      v-if="allAssetsLoaded"
      material="src:../../public/assets/wallpaper.avif"
      color="lightgrey"
      depth="16"
      height="3"
      width="0"
      position="-4 1.4 -5"
    ></a-box>

    <a-box
      v-if="allAssetsLoaded"
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
      clickable
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

    <TheManageDoor v-if="allAssetsLoaded" position="0 1.36 -13" />

    <TheNavMesh />

    <TheCameraRig />
  </a-scene>
</template>
