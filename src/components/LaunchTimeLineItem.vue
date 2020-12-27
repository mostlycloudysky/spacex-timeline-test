<template>
  <v-timeline-item>
    <template v-slot:icon>
      <v-avatar>
        <img :src="launch.links.mission_patch_small" />
      </v-avatar>
    </template>
    <template v-slot:opposite>
      <span>{{ launchDate }}</span>
    </template>
    <v-card class="elevation-2">
      <v-card-title class="headline">
        Mission: {{ launch.mission_name }}
      </v-card-title>
      <v-card-subtitle>
        Rocket: {{ launch.rocket.rocket_name }}
      </v-card-subtitle>
      <v-card-text>
        {{ launch.details }}
      </v-card-text>
    </v-card>
  </v-timeline-item>
</template>

<script>
import moment from "moment";
export default {
  name: "LaunchTimeLineItem",
  props: ["launch"],
  computed: {
    launchData() {
      return moment(this.launch.launch_date_local).format("mm/dd/yyyy");
    }
  }
};
</script>

<style></style>
