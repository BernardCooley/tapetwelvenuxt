<template>
  <div class="videosContainer">
    <div id="videos" class="videosPageContainer" fxLayout="column">
      <div class="videoContainer">
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/peCQwX_JCpY" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/WU3Ym6MwpZU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/5b9AA5gbaX0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/6EjrdBd08VU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/PrnI1QCj7jM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/EivBI--j8Io" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <div class="video">
          <iframe width="360" height="200" src="https://www.youtube.com/embed/FghcZLpnIb0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.videoContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.video {
  margin: 10px;
}
</style>
