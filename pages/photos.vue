<template>
  <div class="photosContainer">
    <div id="photos" class="imagesPageContainer" fxLayout="column">

      <div fxShow class="ImageContainer" fxLayoutWrap>
        <img src="assets/images/photos/emom-1.jpg">
        <img src="assets/images/photos/celtronic.jpg">
        <img src="assets/images/photos/hoxton.jpg">
        <img src="assets/images/photos/keyboards.jpg">
        <img src="assets/images/photos/roddens.jpg">
        <img src="assets/images/photos/silk-halloween.jpg">
        <img src="assets/images/photos/wired-show.jpg">
        <img src="assets/images/photos/records.jpg">
  </div>
      </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
img {
  max-width: 350px;
  padding: 10px;
  margin: 20px;
  border: 1px solid rgb(100, 100, 100);
}

.imagesPageContainer {
  text-align: center;
}
</style>
