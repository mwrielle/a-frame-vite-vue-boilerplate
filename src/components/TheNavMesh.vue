<template>
  <a-entity
    id="room"
    geometry="primitive: plane; height: 15.5; width: 6"
    position="0 0 -4.75"
    rotation="-90 0 0"
    data-role="nav-mesh"
    visible="true"
  ></a-entity>

  <a-entity
    id="forest"
    geometry="primitive: plane; height: 30; width: 30"
    position="0 10 0"
    rotation="-90 0 0"
    material="color:#333"
    data-role="nav-mesh"
    visible="true"
  ></a-entity>
</template>
