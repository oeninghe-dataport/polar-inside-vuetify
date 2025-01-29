<template>
  <div
    style="
      width: 680px;
      height: 420px;
      position: relative;
    "
    id="polarstern"
  >
    <!-- Optional, may use if your page does not have its own <noscript> information -->
    <noscript>Please use a browser with active JavaScript to use the map client.</noscript>
  </div>
  <v-btn @click="loadMap">Laden</v-btn>
</template>

<script setup>
import mapClient from '@polar/client-generic'
function loadMap() {
  mapClient.createMap({
    containerId: 'polarstern',
    //services: 'https://geodienste.hamburg.de/services-internet.json',
    services: '/services.json',
    enabledPlugins: [
      'loading-indicator',
    ],
    mapConfiguration: {
      epsg: "EPSG:25832",
      layers: [{
        id: '453',
        visibility: true,
        type: 'background',
      }],
      stylePath: './node_modules/@polar/client-generic/dist/polar-client.css',
      loadingIndicator: {
        displayComponent: true,
      },
    },
  })
}
</script>
