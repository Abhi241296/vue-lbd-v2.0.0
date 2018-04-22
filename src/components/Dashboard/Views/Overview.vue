<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xl-3 col-md-6">
          <stats-card>
            <div slot="header" class="icon-warning">
              <i class="nc-icon nc-chart text-info"></i>
            </div>
            <div slot="content">
              <p class="card-category">Accuracy Score</p>
              <h4 class="card-title" id="ac1">1</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-refresh"></i>Updated now
            </div>
          </stats-card>
        </div>

        <div class="col-xl-3 col-md-6">
          <stats-card>
            <div slot="header" class="icon-success">
              <i class="nc-icon nc-light-3 text-success"></i>
            </div>
            <div slot="content">
              <p class="card-category">Execution Time</p>
              <h4 class="card-title" id="ex">3 s</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-calendar-o"></i>Updated now
            </div>
          </stats-card>
        </div>

        <div class="col-xl-3 col-md-6" v-show ="!isVisible">
          <stats-card>
            <div slot="header" class="icon-danger">
              <i class="nc-icon nc-chart text-success"></i>
            </div>
            <div slot="content">
              <p class="card-category">Accuracy Score</p>
              <h4 class="card-title" id="ac2">-</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-clock-o"></i>Updated now
            </div>
          </stats-card>
        </div>

        <div class="col-xl-3 col-md-6" v-show ="!isVisible">
          <stats-card>
            <div slot="header" class="icon-info">
              <i class="nc-icon nc-favourite-28 text-primary"></i>
            </div>
            <div slot="content">
              <p class="card-category">Sentiment Score</p>
              <h4 class="card-title" id="ss">-</h4>
            </div>
            <div slot="footer">
              <i class="fa fa-refresh"></i>Updated now
            </div>
          </stats-card>
        </div>

      </div>

      <div class="row">
        <div class="col-md-8" id="training">
            <img src ='../../../../static/img/linear_train.png'>
            <template slot="header">
              <h4 class="card-title">Users Behavior</h4>
              <p class="card-category">24 Hours performance</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Open
                <i class="fa fa-circle text-danger"></i> Click
                <i class="fa fa-circle text-warning"></i> Click Second Time
              </div>
              <hr>
              <div class="stats">
                <i class="fa fa-history"></i> Updated 3 minutes ago
              </div>
            </template>
        </div>

        <div class="col-md-4" id="cm">
          <chart-card :chart-data="pieChart.data" chart-type="Pie">
            <template slot="header">
              <h4 class="card-title">Train/Test Split</h4>
              <p class="card-category">Simple Linear Regression</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Train
                <i class="fa fa-circle text-danger"></i> Test
              </div>
              <hr>
              <div class="stats">
                <i class="fa fa-clock-o"></i> Updated now
              </div>
            </template>
          </chart-card>
        </div>
      </div>

      <div class="row">
        <div class="col-md-8" id="testing">
            <img src ='../../../../static/img/linear_test.png'>
            <template slot="header">
              <h4 class="card-title">2014 Sales</h4>
              <p class="card-category">All products including Taxes</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <i class="fa fa-circle text-info"></i> Tesla Model S
                <i class="fa fa-circle text-danger"></i> BMW 5 Series
              </div>
              <hr>
              <div class="stats">
                <i class="fa fa-check"></i> Data information certified
              </div>
            </template>
          </chart-card>
        </div>

        <div class="col-md-4">
          <card>
            <template slot="header">
              <h5 class="title">Algorithms</h5>
              <p class="category">Click to view output</p>
            </template>
            <table>
                <tr>
                  <td>Linear Regression</td><td v-on:click ="output1">View</td>
                </tr>
                <tr>
                  <td>Logistic Regression</td><td v-on:click ="output2">View</td>
                </tr><tr>
                  <td>SVM</td><td v-on:click ="output3">View</td>
                </tr><tr>
                  <td>Decision Tree Classifier</td><td v-on:click ="output4">View</td>
                </tr><tr>
                  <td>Decision Tree & Random Forest w/ Ratings</td><td v-on:click ="output5">View</td>
                </tr><tr>
                  <td>Decision Tree & Random Forest w/o Ratings</td><td v-on:click ="output6">View</td>
                </tr>
            </table>
            <div class="footer">
              <hr>
              <div class="stats">
                <i class="fa fa-history"></i> Updated now
              </div>
            </div>
          </card>

        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import ChartCard from 'src/components/UIComponents/Cards/ChartCard.vue'
  import StatsCard from 'src/components/UIComponents/Cards/StatsCard.vue'
  import Card from 'src/components/UIComponents/Cards/Card.vue'
  import LTable from 'src/components/UIComponents/Table.vue'

  export default {
    components: {
      Card,
      LTable,
      ChartCard,
      StatsCard
    },

    methods: {

      output1 () {
        document.getElementById('training').innerHTML = "<img src='../../../../static/img/linear_train.png' />"
        document.getElementById('testing').innerHTML = "<img src='../../../../static/img/linear_test.png' />"
        document.getElementById('ac1').innerHTML = '1'
        document.getElementById('ex').innerHTML = '3 s'
        document.getElementById('ac2').innerHTML = '-'
        document.getElementById('ss').innerHTML = '-'
      },

      output2 () {
        document.getElementById('training').innerHTML = "<img src='../../../../static/img/logistic_train.png' />"
        document.getElementById('testing').innerHTML = "<img src='../../../../static/img/logistic_test.png' />"
        document.getElementById('cm').innerHTML = "<img src='../../../../static/img/cm_logistic.png' />"
        document.getElementById('ac1').innerHTML = '0.89'
        document.getElementById('ex').innerHTML = '2 s'
        document.getElementById('ac2').innerHTML = '-'
        document.getElementById('ss').innerHTML = '-'
      },

      output3 () {
        document.getElementById('training').innerHTML = "<img src='../../../../static/img/SVM_train.png' />"
        document.getElementById('testing').innerHTML = "<img src='../../../../static/img/SVM_test.png' />"
        document.getElementById('cm').innerHTML = "<img src='../../../../static/img/cm_svr.png' />"
        document.getElementById('ac1').innerHTML = '0.9'
        document.getElementById('ex').innerHTML = '1 s'
        document.getElementById('ac2').innerHTML = '-'
        document.getElementById('ss').innerHTML = '-'
      },

      output4 () {
        document.getElementById('training').innerHTML = "<img src='../../../../static/img/tree.png' />"
        document.getElementById('testing').innerHTML = "<img src='../../../../static/img/dt.png' />"
        document.getElementById('cm').innerHTML = "<img src='../../../../static/img/cm.png' />"
        document.getElementById('ac1').innerHTML = '0.99951'
        document.getElementById('ex').innerHTML = '3 s'
        document.getElementById('ac2').innerHTML = '-'
        document.getElementById('ss').innerHTML = '-'
      },

      output5 () {
        document.getElementById('training').innerHTML = "<img src='../../../../static/img/decision_random_wr.png' />"
        document.getElementById('testing').innerHTML = "<img src='../../../../static/img/decision_random_wtr.png' />"
        document.getElementById('ac1').innerHTML = '0.2432'
        document.getElementById('ex').innerHTML = '20 s'
        document.getElementById('ac2').innerHTML = '0.49536'
        document.getElementById('ss').innerHTML = '0.0345'
      },

      output6 () {
        document.getElementById('training').innerHTML = "<img src='../../../../static/img/decision_random_wr.png' />"
        document.getElementById('testing').innerHTML = "<img src='../../../../static/img/decision_random_wtr.png' />"
        document.getElementById('ac1').innerHTML = '0.214981'
        document.getElementById('ex').innerHTML = '20 s'
        document.getElementById('ac2').innerHTML = '0.4915'
        document.getElementById('ss').innerHTML = '-'
      }
    },
    data () {
      return {
        pieChart: {
          data: {
            labels: ['67%', '33%'],
            series: [67, 33]
          }
        },
        tableData: {
          data: [
            {title: 'Linear Regression', train: '../../../../static/img/linear_train.png', test: '../../../../static/img/linear_test.png'},
            {title: 'Logistic Regression', train: '../../../../static/img/logistic_train.png', test: '../../../../static/img/logistic_test.png'},
            {title: 'SVM', train: '../../../../static/img/SVM_train.png', test: '../../../../static/img/SVM_test.png'},
            {title: 'Decision Tree Classifier', train: '../../../../static/img/tree.png'},
            {title: 'Decision Tree and Random Forest with Ratings', train: '../../../../static/img/decision_random_wr.png'},
            {title: 'Decision Tree and Random Forest without Ratings', train: '../../../../static/img/decision_random_wtr.png'}
          ]
        }
      }
    }
  }
</script>
<style>

</style>
