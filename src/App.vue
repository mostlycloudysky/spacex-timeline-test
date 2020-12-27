<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <h2>SpaceX Launcher test</h2>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-content>
      <v-container>
        <v-timeline v-if="launches.length > 0">
          <LaunchTimeLineItem
            v-for="launch in launches"
            :key="launch.flight_number"
            :launch="launch"
          />
        </v-timeline>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import axios from "axios";
import LaunchTimeLineItem from "./components/LaunchTimeLineItem";
export default {
  name: "App",

  components: {
    LaunchTimeLineItem
  },

  data: () => ({
    launches: []
  }),
  created() {
    axios.get("https://api.spacexdata.com/v3/launches/past").then(response => {
      this.launches = response.data;
    });
  }
};
</script>
