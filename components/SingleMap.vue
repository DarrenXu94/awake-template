<template>
  <div>
    <div class="page-wrapper map-page container">
      <div id="map-wrap" style="height: 100%">
        <client-only>
          <l-map :zoom="17" :center="formatLocation" ref="leaflet">
            <l-tile-layer
              url="https://{s}.tile.osm.org/{z}/{x}/{y}.png"
            ></l-tile-layer>
            <l-marker :lat-lng="formatLocation" @ready="(e) => checkAndOpen(e)">
              <l-popup>
                <div>
                  {{ name }}
                </div>
              </l-popup>
            </l-marker>
          </l-map>
        </client-only>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SingleMap',
  components: {},
  props: {
    location: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    }
  },
  data() {
    return {}
  },
  computed: {
    formatLocation() {
      return (
        this.location
          .split(' ')
          // eslint-disable-next-line arrow-parens
          .map((val) => parseFloat(val))
      )
    }
  },
  methods: {
    checkAndOpen(mapObject) {
      mapObject.openPopup()
    }
  },
  mounted() {
    setTimeout(() => {
      console.log(this.$refs.leaflet)
      this.$refs.leaflet.mapObject.invalidateSize()
    }, 100)
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
