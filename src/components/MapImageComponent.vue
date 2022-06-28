<template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="12">
        <v-card-actions>
          <v-slide-group v-model="mapSelected">
            <v-slide-item
              v-for="(item, index) in mapList"
              :key="index"
              v-slot="{ active, toggle }"
            >
              <v-btn
                large
                rounded
                class="mr-2"
                :input-value="active"
                active-class="secondary white--tex"
                @click="toggle"
              >
                {{ item.text }}
              </v-btn>
            </v-slide-item>
          </v-slide-group>
        </v-card-actions>
        <v-card-text>
            <animation-component :map="mapList[mapSelected]"></animation-component>
        </v-card-text>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import AnimationComponent from "./AnimationComponent.vue";
export default {
  name: "MapImageComponent",
  components: { AnimationComponent },
  data: () => ({
    mapSelected: 0,
    mapList: [{ text: "Mapa 1" }, { text: "Mapa 2" }, { text: "Mapa 3" }],
  }),
};
</script>

<style></style>
AnimationComponent
