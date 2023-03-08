<template>
  <div class="page-wrapper map-page container">
    <div id="map-wrap" style="height: 100%">
      <client-only>
        <l-map :zoom="16" :center="[-35.28608957097441, 149.11992525975597]">
          <l-tile-layer
            url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"
          ></l-tile-layer>
          <l-marker
            v-for="point in locations"
            :key="point.name"
            :lat-lng="point.latlon"
          >
            <l-popup>
              <div>
                {{ point.name }}
              </div>
            </l-popup>
          </l-marker>
        </l-map>
      </client-only>
    </div>
  </div>
</template>

<script>
const locations = [
  { name: 'malatang', latlon: [-35.2783192, 149.1270956] },
  { name: 'terra', latlon: [-35.27863005347709, 149.12695721534584] }
]
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
