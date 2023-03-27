<template>
  <div class="tier" :class="`tier-${ranking}`">
    <!-- <b> Tier: {{ ranking }} </b> -->
    <img
      :src="`./tier-logos/${ranking}-tier.png`"
      :alt="`tier-${ranking} logo`"
    />
  </div>
</template>
<script>
export default {
  name: 'TierList',
  props: {
    ranking: {
      type: String,
      required: true
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
