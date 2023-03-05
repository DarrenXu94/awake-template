<template>
  <div class="page-wrapper map-page container">
    <!-- <site-hero
      title="Map"
      subtitle="Where is everything?"
      image="/uploads/lunch.jpeg"
    ></site-hero> -->

    <div id="map-wrap" style="height: 100%">
      <client-only>
        <l-map :zoom="13" :center="[-35.28608957097441, 149.11992525975597]">
          <l-tile-layer
            url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"
          ></l-tile-layer>
          <!-- <l-marker :lat-lng="[55.9464418, 8.1277591]"></l-marker> -->
          <l-marker
            v-for="point in locations"
            :key="point[0]"
            :lat-lng="point"
          ></l-marker>
        </l-map>
      </client-only>
    </div>
  </div>
</template>

<script>
const locations = [[-35.2783192, 149.1270956]]
export default {
  components: {},
  data() {
    return { locations }
  }
}
</script>

<style lang="scss">
.map-page {
  margin-top: 52px;

  position: relative;
  z-index: 1;
  height: 80vh;
}
</style>
