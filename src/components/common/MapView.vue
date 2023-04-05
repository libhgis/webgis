<template>
  <div id="map-view"></div>
</template>

<script>
import { loadModules } from 'esri-loader'

const options = {
  url: 'https://js.arcgis.com/4.26/init.js',
  css: 'https://js.arcgis.com/4.26/esri/themes/light/main.css',
}

export default {
  name: 'MapView',
  components: {},
  mounted: function () {
    this._createMapView();
  },
  methods: {
    async _createMapView() {
      const [Map, MapView] = await loadModules(['esri/Map', 'esri/views/MapView'], options)

      const map = new Map({
        basemap: 'osm',
      })

      const view = new MapView({
        container: 'map-view',
        map: map,
        zoom: 10,
        center: [87.747115, 43.853624],
      })

      view.ui.components = []

      console.log(view)
    }
  }

};
</script>

<style>
#map-view {
  position: relative;
  width: 100%;
  height: 100%;
}
</style>
