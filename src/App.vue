<template>
  <!-- Vue-App (App.vue) -->
  <v-app>
    <!-- App bar (Header-Bar) -->
    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Divelog</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-avatar size="48" color="primary lighten-2" rounded>
            <v-btn icon x-large v-on="on">
              <v-icon>mdi-account-circle</v-icon>
            </v-btn>
          </v-avatar>
        </template>
        <v-list>
          <v-list-item>
            <v-btn text>Profile</v-btn>
          </v-list-item>
          <v-divider></v-divider>
          <v-list-item>
            <v-btn text color="red">Logout</v-btn>
          </v-list-item>
        </v-list>
      </v-menu>

      <template v-slot:extension>
        <v-tabs centered>
          <v-tab>Logbook</v-tab>
          <v-tab disabled>Tab 2</v-tab>
          <v-tab disabled>Tab 3</v-tab>
        </v-tabs>
      </template>
    </v-app-bar>

    <!-- Main content of the app; Sizing based upon apps components -->
    <v-main>
      <!-- Provides the application with the proper gutter -->
      <v-container>
        <new-dive-formular @save-new-dive="saveNewDive"></new-dive-formular>
        <br />
        <v-divider></v-divider>
        <br />
        <dive-card
          v-for="dive in diveList"
          v-bind="dive"
          :key="dive.id"
        ></dive-card>

        <!-- If usinig vue-router: -->
        <!-- <router-view></router-view> -->
      </v-container>
    </v-main>

    <!-- Footer area -->
    <v-footer app color="light-grey" inset absolute>
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} – <strong>Divelog</strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
import DiveCard from "./components/DiveCard.vue";
import NewDiveFormular from "./components/NewDiveFormular.vue";
// import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",

  components: {
    DiveCard,
    NewDiveFormular,
    //HelloWorld,
  },

  data: () => ({
    diveList: [
      {
        id: 0,
        country: "Egypt",
        divesite: "Dar 'es Saalam",
        startDateTime: "2021-12-13T15:00:00.00Z",
        durationInMins: "15",
      },
    ],
  }),

  methods: {
    saveNewDive: function (dive) {
      dive.id = this.diveList.length;
      this.diveList.push(dive);
    },
  },
};
</script>
