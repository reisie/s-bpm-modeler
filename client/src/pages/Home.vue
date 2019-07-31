<template>
  <v-container fluid>
    <v-layout row wrap>
      <v-flex xs12 sm12 md8 offset-md2 class="mb-5">
        <v-toolbar dark class="primary">
          <v-toolbar-title class="headline">SO-PASS Process Modeler</v-toolbar-title>
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
          <div class="text-xs-center display-3 mb-3">SO-PASS Process Modeler</div>
          <div class="text-xs-center headline mb-5">
            Create, import and export subject-orientated process models using the Parallel Activity Specification Scheme (PASS).</br>
            Compatible with I2PM Standard PASS Ontology 1.0.</br></br>
            Based on <a href="https://github.com/mkolodiy/s-bpm-modeler/">S-BPM-modeler by Maksym Kolodiy</a>.
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
            <v-btn primary large v-on:click="tempLogin">
              <v-icon dark class="pr-2">fa-clock-o</v-icon>
              Explore with temporary account
            </v-btn>
          </div>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import {mapActions} from 'vuex'
  export default {
    name: 'Home',
    data () {
      return {
        user: {
          firstName: 'Temporary Account',
          lastName: 'Temporary Account',
          // TODO: replace random-string-generation by something more robust
          email: Math.random().toString(36).substring(2, 15) + '@tempaccount.invalid',
          password: Math.random().toString(36).substring(2, 15),
          strategy: 'local'
        }
      }
    },
    methods: {
      ...mapActions('auth', ['register']),
      ...mapActions('auth', ['login']),
      tempLogin: function (event) {
        // TODO: account should be deleted by garbage collector in server
        this.register(this.user)
          .then(response => {
            this.sendNotification('Temporary registration successful, logging on...', null, 'success')
            this.login(this.user)
              .then(response => {
                this.$router.replace({path: '/main/dashboard'})
              })
              .catch(() => {
                this.sendNotification('Login failed', 'Something went wrong.', 'error')
                this.$router.replace({path: '/login'})
              })
          })
          .catch(() => {
            this.sendNotification('Registration failed', 'Something went wrong.', 'error')
          })
      },
      sendNotification (title, text, type) {
        this.$notify({
          title: title,
          text: text,
          group: 'v-notifications',
          type: type
        })
      }
    }
  }
</script>

<style lang="sass" scoped>
</style>
