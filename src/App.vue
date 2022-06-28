<template>
  <v-app>
    <v-app-bar app dark>
      <v-toolbar>
        <v-toolbar-title>Slider Map Vuetify</v-toolbar-title>
      </v-toolbar>
    </v-app-bar>

    <v-main>
      <map-image-component></map-image-component>
    </v-main>
  </v-app>
</template>

<script>
import MapImageComponent from "./components/MapImageComponent.vue";
export default {
  name: "App",

  components: { MapImageComponent },

  data: () => ({
    //
  }),
};
</script>
