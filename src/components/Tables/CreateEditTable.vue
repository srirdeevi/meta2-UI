<template>
  <!-- <div class="hello">
    <h5>{{ msg }}, your id is {{ id }}</h5>
    <h1 v-if="id === 'new'">This is create table page</h1>
    <h1 v-else>this is edit table page</h1>
  </div> -->
  <v-container fluid>
    <v-toolbar dense>
      <v-toolbar-title>
        Table Metadata
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn dense>Save</v-btn>
    </v-toolbar>
    <v-tabs color="grey" dark slider-color="white" class="pt-4 text-transform-none">
      <v-tab ripple>
        Basics
      </v-tab>
      <v-tab ripple>
        Headnotes/Footnotes
      </v-tab>
      <v-tab ripple @click="onTabChange()">
        Dimensions
      </v-tab>
      <v-tab-item>
        <v-card flat>
          <v-card-text>
            <table-basic-metadata></table-basic-metadata>
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat>
          <v-card-text><table-notes></table-notes></v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat>
          <v-card-text>
            <dimensions></dimensions>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
  </v-container>
</template>

<script>
  import router from '../../router/index'
  import TableBasicMetadata from './TableBasicMetadata.vue'
  import TableNotes from './TableNotes.vue'
  import Dimensions from './Dimensions.vue'
  import { mapGetters } from 'vuex'
  export default {
    name: 'CreateEditTable',
    components: {
      TableBasicMetadata,
      TableNotes,
      Dimensions
    },
    data () {
      return {
        debug: false,
        id: 0,
        msg: 'META2'
      }
    },
    watch: {
      '$route' (to, from) {
        this.id = to.params.id
      }
    },
    created () {
      this.id = this.$route.params.tableString
      console.log(this.id)
    },
    methods: {
      navigate () {
        router.go(-1)
      },
      onTabChange () {
        /* // Case when route was used once or more
        this.$router.push({ path: '/' }).then(
        () => {
          this.$router.push({ path: '/edittable/new' })
        }) */
        this.$store.dispatch('getDimensionsList')
      }
    },
    computed: {
      ...mapGetters([
        'selectedProgramId',
        'selectedComponentId',
        'selectedDatasetId'
      ]),
      dimensionsList () {
        console.log('------------gets the list of dimenssions')
        console.log(this.$store.state.dimensionsList)
        return this.$store.state.dimensionsList
      }
    }
  }
</script>
<!-- Add "scoped" attribute to limit css to this component only -->
<style scoped>
  text-transform-none {
    text-transform: none !important;
  }
</style>
