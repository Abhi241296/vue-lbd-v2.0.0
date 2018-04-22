<template>
  <div class="content">
    <div class="container-fluid">
      <card>
        <template slot="header">
          <h4 class="card-title">Video Games Sales Dataset</h4>
          <p class="card-category">Containing sales data as at 22 December 2016</p>
        </template>
        <template>
        <div class="app">
          <h3>Example - Import file with required login, firstname, lastname and optional values</h3>
          <br>
          <xls-csv-parser :columns="columns" @on-validate="onValidate" :help="help" lang="en"></xls-csv-parser>
          <br><br>
          <div class="results" v-if="results">
            <h3>Results:</h3>
            <pre>{{ JSON.stringify(results, null, 2) }}</pre>
          </div>
        </div>
      </template>
      </card>
    </div>
  </div>
</template>
<script>
  import Card from 'src/components/UIComponents/Cards/Card.vue'
  import { XlsCsvParser } from 'vue-xls-csv-parser'

  export default {
    name: 'App',
    components: {
      XlsCsvParser, Card
    },
    methods: {
      notifyVue (verticalAlign, horizontalAlign) {
        const notification = {
          template: `<span>Welcome to <b>Light Bootstrap Dashboard</b> - a beautiful freebie for every web developer.</span>`
        }

        const color = Math.floor((Math.random() * 4) + 1)
        this.$notifications.notify(
          {
            component: notification,
            icon: 'nc-icon nc-app',
            horizontalAlign: horizontalAlign,
            verticalAlign: verticalAlign,
            type: this.type[color]
          })
      },
      onValidate (results) {
        this.results = results
      }
    },
    data () {
      return {
        columns: [
          { name: 'ID', value: 'ID' },
          { name: 'Name', value: 'Name' },
          { name: 'Platform', value: 'Platform' },
          { name: 'Year_of_Release', value: 'Year_of_Release' },
          { name: 'Genre', value: 'Genre' },
          { name: 'Publisher', value: 'Publisher' },
          { name: 'Global_Sales', value: 'Global_Sales' },
          { name: 'Critic_Score', value: 'Critic_Score' },
          { name: 'Critic_Count', value: 'Critic_Count' },
          { name: 'User_Score', value: 'User_Score' },
          { name: 'User_Count', value: 'User_Count' },
          { name: 'Developer', value: 'Developer' },
          { name: 'Rating', value: 'Rating' },
          { name: 'Other', value: 'other', isOptional: true }
        ],
        results: null,
        help: 'Necessary columns are: login, firstname and lastname',
        type: ['', 'info', 'success', 'warning', 'danger'],
        notifications: {
          topCenter: false
        }
      }
    }
  }
</script>
<style lang="scss">

</style>