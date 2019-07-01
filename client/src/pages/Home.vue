<template>
  <v-container fluid>
    <v-layout row wrap>
      <v-flex xs12 sm12 md8 offset-md2 class="mb-5">
        <v-toolbar dark class="primary">
          <v-toolbar-title class="headline">S-BPM Modeler</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-btn flat to="/login">
              <v-icon dark class="pr-2">fa-sign-in</v-icon>
              Log in
            </v-btn>
            <v-btn flat to="/register">
              <v-icon dark class="pr-2">fa-user-plus</v-icon>
              Register
            </v-btn>
          </v-toolbar-items>
        </v-toolbar>
      </v-flex>
      <v-flex xs12 sm12 md8 offset-md2 class="mb-5">
        <v-card class="pa-5">
          <div class="text-xs-center display-3 mb-3">S-BPM Modeler</div>
          <div class="text-xs-center headline mb-5">
            Create, Import and Export S-BPM / I2PM PASS processes based on Web Ontology Language
          </div>
          <div class="text-xs-center">
            <v-btn primary large to="/login">
              <v-icon dark class="pr-2">fa-sign-in</v-icon>
              Log in
            </v-btn>
            <v-btn primary large to="/register">
              <v-icon dark class="pr-2">fa-user-plus</v-icon>
              Register
            </v-btn>
          </div>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    name: 'Home'
  }
</script>

<style lang="sass" scoped>
</style>
