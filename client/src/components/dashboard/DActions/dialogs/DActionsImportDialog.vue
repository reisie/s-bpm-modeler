<template>
  <v-container fluid>
    <v-layout row wrap>
      <v-flex>
        <v-dialog v-model="isOpen" width="500">
          <v-card>
            <v-card-title class="headline">
              Import
            </v-card-title>
            <v-card-text>
              <p class="body-2 pt-3">Please select a file that should be imported*:</p>
              <input type="file" @change="onFileChange">
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn flat primary @click.native="importFile()">Import</v-btn>
              <v-btn flat error @click.native="hide()">Close</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  import rdflibService from '@/rdflib-services/rdflib-service'
  import {mapActions} from 'vuex'
  export default {
    name: 'DActionsImportDialog',
    data () {
      return {
        isOpen: false,
        fileAsString: null,
        fileName: null,
        standardOnt: true,
        customOnt: false
      }
    },
    methods: {
      ...mapActions('common', ['setDataLoading']),
      show () {
        this.isOpen = true
      },
      hide () {
        this.reset()
        this.isOpen = false
      },
      onFileChange (e) {
        const files = e.target.files || e.dataTransfer.files
        const reader = new FileReader()

        this.fileName = files[0].name

        reader.onload = (e) => {
          this.fileAsString = e.target.result
        }

        reader.readAsText(files[0])
      },
      importFile () {
        if (this.fileName !== null && this.fileAsString !== null) {
          rdflibService.import(this.standardOnt, this.customOnt, this.fileName, this.fileAsString)
          this.setDataLoading(true)
          this.hide()
        }
      },
      reset () {
        this.standardOnt = true
        this.customOnt = false
        this.fileAsString = null
        this.fileName = null
      }
    }
  }
</script>

<style lang="scss" scoped>
</style>
