<template>
  <v-row dense>
    <v-col cols="12">
      <v-card elevation="2" outlined>
        <v-card-title>{{ divesite }}</v-card-title>
        <v-card-subtitle>{{ country }}</v-card-subtitle>
        <v-card-text>
          <div>Dive time: {{ durationInMins }} mins</div>
          <div>Time start dive: {{ startDateTime }}</div>
          <div>Time end dive: {{ endDateTime }}</div>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="deep-purple" text> Show more </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "DiveCard",

  props: {
    id: Number,
    country: String,
    divesite: String,
    startDateTime: String,
    durationInMins: String,
  },

  data: () => ({}),

  computed: {
    endDateTime: function () {
      return this.$props.startDateTime;
    },
  },
};
</script>
