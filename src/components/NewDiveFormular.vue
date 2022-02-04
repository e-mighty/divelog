<template>
  <v-form ref="form">
    <v-text-field
      label="Dive site"
      filled
      :rules="[rules.required]"
      v-model="dive.divesite"
    ></v-text-field>
    <v-text-field label="Country" filled v-model="dive.country"></v-text-field>
    <v-date-picker
      show-adjacent-months
      elevation="4"
      v-model="dive.startDateTime"
      full-width
      max="Date.now().toString().substr(0, 10)"
    ></v-date-picker>
    <br />
    <v-text-field
      label="Duration of dive (mins)"
      filled
      v-model="dive.durationInMins"
      :type="'number'"
    ></v-text-field>
    <v-btn block color="green outlined" @click="submit"> Save </v-btn>
  </v-form>
</template>

<script>
export default {
  name: "NewDiveFormular",

  data: () => ({
    dive: {
      id: null,
      country: null,
      divesite: null,
      startDateTime: null,
      durationInMins: null,
    },
    rules: {
      required: (value) => !!value || "Required",
    },
  }),

  methods: {
    submit: function (event) {
      event.preventDefault();

      if (this.$refs.form.validate()) {
        const diveData = {
          id: this.dive.id,
          country: this.dive.country,
          divesite: this.dive.divesite,
          startDateTime: this.dive.startDateTime,
          durationInMins: this.dive.durationInMins,
        };

        this.$emit("save-new-dive", diveData);
        this.$refs.form.reset();
      }
    },
  },
};
</script>
