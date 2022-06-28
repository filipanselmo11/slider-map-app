<template>
  <v-row align="center" justify="center">
    <v-col cols="12" align="center" align-self="center" min-height="600">
      <transition name="fade-slide">
        <div v-for="index in [currentIndex]" :key="index">
          <v-img max-height="600" max-width="1200" :src="currentMap" />
        </div>
      </transition>
    </v-col>
    <v-col cols="12">
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
  props: {
    map: {
      type: Object,
    },
  },
  data: () => ({
    play: false,
    timer: undefined,
    currentIndex: undefined,
    maps: [],
    map1: [require("../assets/mapa-1.jpg"), require("../assets/mapa-2.jpg"), require("../assets/mapa-3.png")],
    map2: [require("../assets/mapa-4.jpg"), require("../assets/mapa-5.png"), require("../assets/mapa-6.png")],
    map3: [require("../assets/mapa-7.png"), require("../assets/mapa-8.png"), require("../assets/mapa-9.png")],
  }),
  watch: {
    map(value) {
      if (value) {
        this.play = false;
        this.clearAnimationInterval();
        this.currentIndex = 0;
        this.verifyMap();
      }
    },
  },
  mounted() {
    this.verifyMap();
  },

  computed: {
    startMap() {
      return 0;
    },
    currentMap() {
      return this.maps[Math.abs(this.currentIndex) % this.maps.length];
    },

    endMap() {
      return this.maps.length - 1;
    },
  },
  methods: {
    verifyMap() {
      if (this.map.text === "Mapa 1") {
        this.maps = [...this.map1];
      } else if (this.map.text === "Mapa 2") {
        this.maps = [...this.map2];
      } else if (this.map.text === "Mapa 3") {
        this.maps = [...this.map3];
      }
    },
    startSlide() {
      this.play = !this.play;
      if (this.play) {
        this.timer = setInterval(() => {
          if (this.currentIndex === this.endMap) {
            this.currentIndex = this.startMap;
          } else {
            this.currentIndex += 1;
          }
        }, 2000);
      } else {
        this.clearAnimationInterval();
      }
    },
    clearAnimationInterval() {
      clearInterval(this.timer);
      this.play = false;
    },
  },
};
</script>

<style scoped>

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}