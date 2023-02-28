<template>
  <div id="home-page" class="page-wrapper home-page">
    <canvas id="my-canvas"></canvas>

    <site-hero :title="title" :subtitle="subtitle" :image="featureImage">
      <!-- <button
        v-if="$siteConfig.newsletter.on"
        class="button is-primary"
        @click="$eventBus.$emit('modal-triggered', 'newsletter-modal')"
      >
        Subscribe To Newsletter
      </button> -->
    </site-hero>
    <main-section theme="one-column">
      <template v-slot:default>
        <!-- All Posts -->
        <posts-grid />
      </template>
      <template v-slot:sidebar>
        Nothing here
      </template>
    </main-section>
    <news-letter-form-modal />
  </div>
</template>

<script>
import ConfettiGenerator from 'confetti-js'
import { mapState } from 'vuex'
import { setPageData } from '../helper'
import NewsLetterFormModal from '~/components/NewsLetterFormModal'

export default {
  name: 'HomePage',
  head() {
    return {
      title: `Home | ${this.$siteConfig.siteName}`
    }
  },
  components: {
    NewsLetterFormModal
  },
  computed: {
    ...mapState(['title', 'subtitle', 'featureImage'])
  },
  fetch({ store, params }) {
    setPageData(store, { slug: 'home' })
  },
  mounted() {
    const confettiSettings = {
      target: 'my-canvas',
      max: 25,
      size: 5,
      clock: 75,
      respawn: false,
      start_from_edge: true,
      rotate: true,
      props: [
        { type: 'svg', src: 'burger.svg' },
        { type: 'svg', src: 'hotdog.svg' },
        { type: 'svg', src: 'pizza.svg' },
        { type: 'svg', src: 'eggplant.svg' },
        { type: 'svg', src: 'icecream.svg' },
        { type: 'svg', src: 'donut.svg' },
        { type: 'svg', src: 'pan.svg' },
        { type: 'svg', src: 'sushi.svg' }
      ]
    }
    const confetti = new ConfettiGenerator(confettiSettings)
    confetti.render()
  }
}
</script>

<style>
.home-page .under-subtitle {
  border-top: none;
  position: relative;
}

#my-canvas {
  position: absolute;
  z-index: 1;
}
</style>
