<template>
  <div id="about-page" class="page-wrapper about-page content-page">
    <site-hero
      title="About Us"
      subtitle="What the heck is this site?"
      image="/uploads/lunch.jpeg"
    ></site-hero>
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <div class="content">
          <h3>What is this?</h3>
          <p>
            Are you always on the lookout for a delicious and affordable
            lunchtime meal? Well, look no further! In this blog, we'll be
            reviewing some of the best lunchtime food deals around, giving you
            the inside scoop on where to find great food at even better prices.
            From fast food chains to local restaurants, we'll be exploring a
            variety of options to suit every taste and budget. Join us as we
            embark on a culinary journey to find the best lunchtime deals in
            town!
          </p>
        </div>
      </template>

      <template v-slot:sidebar>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
<script>
export default {
  head() {
    return {
      title: `About | ${this.$siteConfig.siteName}`
    }
  }
}
</script>
