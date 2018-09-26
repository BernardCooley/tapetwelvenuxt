<template>
  <section class="container">
    <div id="topOfPage"></div>
    <!-- <div> -->
    <!-- <div class="hamburgerContainer" v-on:click='navShow = !navShow'>
        <img id="hamburgerMenuToggle" class="hamburgerMenu" src="/assets/icons/menu_square.png" alt="Menu icon">
      </div>
        <div v-show='navShow'>
          <div class="linksContainer">
            <div class="navList">
              <div class="navListItem" v-for="page in navPages">
                <a pageScroll class="navLink" :href="page.url">{{page.name}}</a>
              </div>
            </div>
          </div>
        </div>
      </div> -->

    <div class="horzNavContainer">
      <div class="navListItem">
        <div class="" v-for="page in navPages">
          <a pageScroll class="navLink" :href="page.url">{{page.name}}</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>

export default {
  data() {
    return {
      navPages: [
        { "url": "home", "name": "Home" },
        { "url": "photos", "name": "Photos" },
        { "url": "videos", "name": "Videos" },
        { "url": "music", "name": "Music" },
        { "url": "contact", "name": "Contact" }
      ],
      navShow: false
    }
  }
}
</script>

<style scoped>
.navListItem {
  display: flex;
  justify-content: flex-end;
  margin-top: 20px;
}

.navList {
  height: 100%;
}

.navLink {
  font-size: 40px;
  text-decoration: none;
  background-color: transparent;
  cursor: pointer;
  padding: 10px;
  margin-top: 15px;
  color: red;
}

.navLink:hover {
  background-color: rgba(173, 173, 173, 0.4);
}

.linksContainer {
  position: fixed;
  left: 0;
  height: 100%;
  border-bottom: 1px solid gray;
  z-index: 1;
  background-color: rgba(32, 32, 32, 0.85);
}

.hamburgerMenu {
  height: 40px;
  padding: 10px 0 0 10px;
  cursor: pointer;
}

.hamburgerContainer {
  height: 70px;
  position: -webkit-sticky;
  position: sticky;
  top: 0;
  left: 0;
}

.pageDivider {
  height: 10px;
  width: 200px;
}

.horzNavContainer {
  padding-right: 50px;
  padding-bottom: 50px;
}
</style>
