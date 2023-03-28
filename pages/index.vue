<template>
  <div id="home-page" class="page-wrapper home-page">
    <div id="tsparticles"></div>

    <site-hero :title="title" :subtitle="subtitle" :image="featureImage">
    </site-hero>
    <main-section theme="one-column">
      <template v-slot:default>
        <posts-grid />
      </template>
      <template v-slot:sidebar>
        Nothing here
      </template>
    </main-section>
    <news-letter-form-modal />
    <keep-alive>
      <Particles />
    </keep-alive>
  </div>
</template>

<script>
import { mapState } from 'vuex'

import { setPageData } from '../helper'
import NewsLetterFormModal from '~/components/NewsLetterFormModal'
import Particles from '~/components/Particles'

export default {
  name: 'HomePage',
  head() {
    return {
      title: `Home | ${this.$siteConfig.siteName}`
    }
  },
  components: {
    NewsLetterFormModal,
    Particles
  },
  computed: {
    ...mapState(['title', 'subtitle', 'featureImage'])
  },
  fetch({ store, params }) {
    setPageData(store, { slug: 'home' })
  }
}
</script>

<style>
.home-page .under-subtitle {
  border-top: none;
  position: relative;
}

/* #my-canvas {
  position: absolute;
  z-index: 1;
} */

#tsparticles {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 1;
  pointer-events: none;
}
</style>
