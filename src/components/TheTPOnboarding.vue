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
      <h1>Forest Project</h1>

      <p v-if="!loaded">loading...</p>
      <button v-if="loaded" @click="enterScene()">Enter scene</button>
      <div class="licences">
        <dl>
          <dt>
            <i>Included</i>
          </dt>
          <dt>
            <a href="https://skfb.ly/6TGAC" target="_blank"
              >oak trees by DJMaesen</a
            >
          </dt>
          <dd>
            <a
              href="http://creativecommons.org/licenses/by/4.0/"
              target="_blank"
              >Licensed under Creative Commons Attribution</a
            >
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
