<template>
  <v-row align="center" justify="center">
    <v-col cols="12" align-self="center" align="center">
      <!-- transicao vai aqui -->
    </v-col>
    <v-col cols="12" align-self="center" align="center">
      <v-slider
        :prepend-icon="play ? 'mdi-pause-circle-outline' : 'mdi-play-circle-outline'"
        @click:prepend="startSlide"
        v-model="currentIndex"
        hide-details
        min="0"
        :max="endMap"
        step="1"
      />
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "AnimationComponent",
  data() {
    return {
      play: false,
      timer: undefined,
      currentIndex: undefined,
      mapImageStartIndex: 0,
      mapImageEndIndex: 2,
      maps: [
        {
          index: 0,
          imageUrl: "../assets/mapa-1.jpg",
        },
        {
          index: 1,
          imageUrl: "../assets/mapa-2.jpg",
        },
        {
          index: 2,
          imageUrl: "../assets/mapa-3.jpg",
        },
      ],
    };
  },
  computed: {
    startMap() {
      return 0;
    },
    currentMap() {
      return this.map[this.currentIndex % this.maps.length];
    },
    endMap() {
      return this.map.length - 1;
    },
  },
  //   props: {
  //     mapItem: {
  //       type: Object,
  //     },
  //   },
};
</script>

<style></style>
