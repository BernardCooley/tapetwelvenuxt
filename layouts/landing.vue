<template>
  <div class="landingPageLayout">
    <div class="layer">
      <nuxt />
    </div>
  </div>
</template>

<style scoped>
.landingPageLayout {
  position: fixed;
  top: 0;
  z-index: -2;
  left: 0;
  right: 0;
  bottom: 0;
  background-size: cover;
  background-position: center;
  background-image: url('~/assets/images/photos/celtronic.jpg');
}
.layer {
  position: fixed;
  top: 0;
  z-index: -1;
  left: 0;
  right: 0;
  bottom: 0;
  background-size: cover;
  background-position: center;
  background-color: rgba(32, 32, 32, 0.85);
}
</style>
