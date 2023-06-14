<template>
  <div class="tier">
    <!-- <b> Tier: {{ ranking }} </b> -->
    <nuxt-link :to="`/categories/${getTier}`">
      <img :src="`/tier-logos/${getTier}.png`" :alt="`${getTier} logo`" />
    </nuxt-link>
  </div>
</template>
<script>
export default {
  name: 'TierList',
  props: {
    categories: {
      type: Array,
      required: true
    }
  },
  computed: {
    getTier() {
      // eslint-disable-next-line arrow-parens
      const tierRanking = this.categories.find((word) => word.endsWith('tier'))
      return tierRanking.replace(' ', '-').toLowerCase()
    }
  }
}
</script>
<style lang="scss" scoped>
.tier {
  font-size: xx-large;

  img {
    max-height: 10rem;
  }
}
</style>
