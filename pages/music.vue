<template>
  <div class="musicContainer">
    <div id="music" class="musicPageContainer">
      <div class="musicContainer">
        <div class="song">
          <iframe style="border: 0; width: 350px; height: 442px;" src="https://bandcamp.com/EmbeddedPlayer/track=1283671493/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/transparent=true/" seamless><a href="http://tapetwelve.bandcamp.com/track/spectral-de-esser">Spectral De-Esser by Tape Twelve</a></iframe>
        </div>
        <div class="song">
          <iframe style="border: 0; width: 350px; height: 470px;" src="https://bandcamp.com/EmbeddedPlayer/album=2700328086/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/transparent=true/" seamless><a href="http://tapetwelve.bandcamp.com/album/string-theory-ep">String Theory EP by Tape Twelve</a></iframe>
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
.musicContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.song {
  margin: 10px;
}
</style>
