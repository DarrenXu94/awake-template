<template>
  <div id="home-page" class="page-wrapper home-page">
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
    <!-- <keep-alive>
      <Particles />
    </keep-alive> -->
  </div>
</template>

<script>
import { mapState } from 'vuex'

import JSConfetti from 'js-confetti'
import { setPageData } from '../helper'
import NewsLetterFormModal from '~/components/NewsLetterFormModal'
// import Particles from '~/components/Particles'

export default {
  name: 'HomePage',
  head() {
    return {
      title: `Home | ${this.$siteConfig.siteName}`
    }
  },
  components: {
    NewsLetterFormModal
    // Particles
  },
  computed: {
    ...mapState(['title', 'subtitle', 'featureImage'])
  },
  fetch({ store, params }) {
    setPageData(store, { slug: 'home' })
  },
  mounted() {
    const jsConfetti = new JSConfetti()

    jsConfetti.addConfetti({
      emojis: ['🍔', '🌯', '🍦', '🍡', '🍱', '🍙', '🍰', '🍟', '🍗', '🍕'],
      emojiSize: 40
    })
  }
}
</script>

<style>
.home-page .under-subtitle {
  border-top: none;
  position: relative;
}
</style>
