<template>
  <section class="container">
    <newsletter></newsletter>
    <social-links></social-links>
  </section>
</template>

<script>
import SocialLinks from '~/components/SocialLinks.vue'
import Newsletter from '~/components/Newsletter.vue'

export default {
  components: {
    SocialLinks,
    Newsletter
  }
}
</script>

<style scoped>
.container {
  background-color: hsla(0, 0%, 68%, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
