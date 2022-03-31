<template>
  <input type="checkbox" v-model="checkbox" /> Show map
  <div class="map-container" v-if="checkbox">
    <l-map :zoom="6" :center="[7, 7]">
      <l-marker
        v-for="(coordinate, i) in coordinates"
        :key="i"
        :lat-lng="coordinate"
      >
        <l-icon :icon-size="[45.25, 45.25]" :icon-anchor="[45.25, 22.62]">
          <div class="custom-marker" />
        </l-icon>
      </l-marker>
    </l-map>
  </div>
</template>

<script setup>
import { LMap, LTileLayer, LMarker, LIcon } from '@vue-leaflet/vue-leaflet'
import 'leaflet/dist/leaflet.css'
import { ref } from 'vue'
const checkbox = ref(true)
const coordinates = []
for (let i = 0; i < 15; i++) {
  for (let ii = 0; ii < 15; ii++) {
    coordinates.push([ii, i])
  }
}
</script>

<style>
.map-container {
  height: 95vh;
}
.custom-marker {
  width: 30px;
  height: 30px;
  border-radius: 50% 50% 50% 0;
  background: rgb(44, 130, 224);
  transform: rotate(-45deg);
  margin: -15px 0 0 -15px;
  border: 1px solid;
}
</style>
