<template>
  <v-app class="contenedor">
    <div class="mb-3">
      <v-row no-gutters class="pa-3">
        <div>
          <span class="font-weight-black">Duplicate sets</span>
          <v-icon small right color="grey lighten-1">error_outline</v-icon>
        </div>
      </v-row>
    </div>
    <v-tabs v-model="tab" background-color="white" color="blue darken-4" left>
      <v-tabs-slider></v-tabs-slider>

      <v-tab>
        <v-col class="text-left mb-3">
          <div class="font-weight-black custom-title mb-1">THIS WEEK</div>
          <v-row no-gutters class="text-lowercase">
            <div class="mr-3">
              <v-icon left>timer</v-icon>30 min
            </div>
            <div>
              <v-icon left>emoji_events</v-icon>320 points
            </div>
          </v-row>
        </v-col>
      </v-tab>

      <v-tab>
        <v-col class="text-left">
          <div class="font-weight-black custom-title mb-1">ADMIN WAITING</div>
          <v-row no-gutters class="text-lowercase">16 duplicates</v-row>
        </v-col>
      </v-tab>

      <v-tabs-items v-model="tab">
        <v-tab-item class="pt-4">
          <duplicatesTable></duplicatesTable>
        </v-tab-item>
        <v-tab-item class="pt-4">
          <v-card style="height: 70vh">
            <v-row no-gutters class="fill-height" align="center" justify="center">
              <div>ADMIN WAITING VIEW</div>
            </v-row>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </v-tabs>
  </v-app>
</template>

<script>
import duplicatesTable from "./components/duplicates";

export default {
  name: "App",
  components: { duplicatesTable },
  data() {
    return {
      tab: null,
      text:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
    };
  }
};
</script>

<style>
.v-tabs-slider-wrapper {
  height: 6px !important;
}
.v-tabs-bar {
  height: 65px !important;
}
.custom-title {
  font-size: 14pt;
}
.contenedor {
  width: 900px;
  max-width: 100%;
  margin: 0 auto;
}
</style>