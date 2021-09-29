<template>
  <v-app app> 
    <v-stepper v-model="page">
      <v-stepper-header>
        <v-stepper-step
          :complete="page >1"
          step="1"
        >
          Input data
        </v-stepper-step>
        <v-divider />
           
        <v-stepper-step
          :complete="page> 2"
          step="2"
        >
          Results
        </v-stepper-step>
      </v-stepper-header>
      <v-stepper-items>
        <v-stepper-content step="2">
          <div
            id="container"
            ref="container"
          >
            <v-mapbox
              v-if="mapContainer"
              id="map"
              ref="map"
              :access-token="accessToken"
              map-style="mapbox://styles/mapbox/light-v9"
              :center="center"
              :zoom="zoom"
              :min-zoom="3"
              container="container"
            />
          </div>
        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>
  </v-app>
</template>


<script>
  import { MapboxMap } from '@deltares/vue-components'

  export default {
    components: {
      MapboxMap,
    },

    data: () => ({
      accessToken: process.env.VUE_APP_MAPBOX_TOKEN,
      page: 2,
      mapContainer: null,
      zoom: 3,
      center: [ 0,0 ],
    }),
    computed: {
      mapConfig() {
        return {
          center: config.map.center,
          zoom: config.map.zoom,
          style: MAP_BASELAYER_DEFAULT.style,
        }
      },
    },
    mounted() {
      this.mapContainer = this.$refs.container
      console.log('mapContainer', this.mapContainer)
    },

  }
</script>

<style lang="scss">
  .mapbox-map__title {
    position: absolute;
    z-index: 1;
    top: $spacing-default;
    left: $spacing-default;
    padding: $spacing-smaller $spacing-small;
    background-color: $color-white;
    user-select: none;
  }

  .mapbox-map__title .text-body-2 {
    margin: 0;
  }

  #map {
    z-index: 5;
  }
  
  #container {
    height: 800px;
  }
</style>
