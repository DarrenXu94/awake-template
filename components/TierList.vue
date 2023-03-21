<template>
  <div class="tier" :class="`tier-${ranking}`">
    <b> Tier: {{ ranking }} </b>
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
}
</style>
