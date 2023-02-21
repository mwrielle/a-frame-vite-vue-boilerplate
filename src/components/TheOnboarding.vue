<script setup>
import { ref } from "vue";

defineProps({
  loaded: Boolean,
});

const showOnboarding = ref(true);

function enterScene() {
  showOnboarding.value = false;
  if (
    AFRAME.utils.device.checkHeadsetConnected() &&
    !AFRAME.utils.device.isMobile()
  ) {
    document.querySelector("a-scene").enterVR();
  }
}
</script>

<template>
  <div id="onboarding" v-if="showOnboarding">
    <div>
      <h1>A-Frame + Vite + Vue Boilerplate</h1>
      <p v-if="!loaded">loading...</p>
      <button v-if="loaded" @click="enterScene()">Enter scene</button>
      <div class="licences">
        <dl>
          <dt>
            <i>Included</i>
          </dt>
          <dt>
            <a
              href="https://sketchfab.com/3d-models/monstera-deliciosa-potted-mid-century-plant-free-1ab9bf841df04c07b1819be596327629"
              target="_blank"
              >Monstera Deliciosa Potted Mid-Century plant free</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>

          <dt>
            <a
              href="https://sketchfab.com/3d-models/potted-plant-1a68fc8877b847c6834ea29a7e65de7a"
              target="_blank"
              >Potted plant</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>

          <dt>
            <a
              href="https://sketchfab.com/3d-models/hoya-ferrii-2c4b059c43214c8cbf7f40e208aa7893"
              target="_blank"
              >Hoya Kerrii</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>

          <dt>
            <a
              href="https://sketchfab.com/3d-models/cc0-etagere-3-75b723b847db4bb4b32f26d5f00d9d92"
              target="_blank"
              >Etagère</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>

          <dt>
            <a
              href="https://sketchfab.com/3d-models/caisse-190490a74c5046bdb66cb4aba2198790"
              target="_blank"
              >Caisse</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>

          <dt>
            <a
              href="https://sketchfab.com/3d-models/sea-shell-742a5f4a7bc84abe8d0c645cdb411cc8"
              target="_blank"
              >Coquillage</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>

          <dt>
            <a
              href="https://www.freepik.com/free-photo/texture-background_1167463.htm#query=parquet%20texture&position=0&from_view=keyword&track=ais"
              target="_blank"
              >Parquet – Image by yingyang on Freepik</a
            >
          </dt>
          <dd>
            <a href="" target="_blank">CC Attribution</a>
          </dd>
        </dl>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-size: 1.5rem;
}
a {
  color: #333;
  text-decoration: none;
}
.licences {
  margin: 2rem 0;
  font-size: 1rem;
  text-align: left;
}
.licences dt {
  padding-top: 0.75rem;
  font-size: 0.9rem;
  font-weight: bold;
}
.licences dd {
  margin-left: 0;
  font-size: 0.8rem;
}

#onboarding {
  position: absolute;
  top: 0;
  left: 0;
  background-color: #eee;
  color: #333;
  width: 100vw;
  height: 100vh;
  padding: 1rem;
  font-family: monospace;
  z-index: 10000;
  overflow: auto;
}
#onboarding > * {
  margin: 0 auto;
  max-width: 50rem;
  width: calc(100vw - 10rem);
  text-align: center;
  border-radius: 0.3rem;
  padding: 1rem;
  font-size: 1.3rem;
}
#onboarding button {
  font-size: 1.3rem;
  padding: 0.5rem 1rem;
  border-radius: 0.3rem;
  background-color: #333;
  color: #eee;
  border: none;
  cursor: pointer;
}
</style>
