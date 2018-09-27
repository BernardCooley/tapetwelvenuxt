<template>
  <div class="defaultLayout">
    <div class="layer">
      <navigation></navigation>
      <nuxt />
      <foot></foot>
    </div>
  </div>
</template>

<script>
import Navigation from '~/components/Navigation.vue'
import Foot from '~/components/Foot.vue'

export default {
  components: {
    Navigation,
    Foot
  }
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css?family=Raleway:200');

.defaultLayout {
  font-family: 'Raleway';
  position: fixed;
  top: 0;
  z-index: -2;
  left: 0;
  right: 0;
  bottom: 0;
  background-size: cover;
  background-position: center;
  background-image: url('~/assets/images/bushes/background-path-desktop.png');
  font-size: 10px;
  color: #bcbcbc;
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
  overflow: scroll;
}
</style>
