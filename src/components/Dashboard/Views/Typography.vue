<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <card>
          <div class="row">
          <div class="col-md-8">
          <chart-card :chart-data="lineChart.data"
                      :chart-options="lineChart.options"
                      :responsive-options="lineChart.responsiveOptions">
            <template slot="header">
              <h4 class="card-title">Sentiment Analysis</h4>
              <p class="card-category">24 Hours performance</p>
            </template>
            <template slot="footer">
              <div class="legend">
                <p class="card-category">Used on Video Games Sales Dataset</p>
                <i class="fa fa-circle text-info"></i> Sentiment Scores
              </div>
              <hr>
              <div class="stats">
                <i class="fa fa-history"></i> Updated now
              </div>
            </template>
          </chart-card>
          </div>
          </div>
          </card>
        </div>

      </div>
    </div>
  </div>
</template>
<script>
  import Card from 'src/components/UIComponents/Cards/Card.vue'
  import ChartCard from 'src/components/UIComponents/Cards/ChartCard.vue'
  export default {
    components: {
      Card,
      ChartCard
    },
    data () {
      return {
        lineChart: {
          data: {
            labels: ['GTA 5', 'Wii Sports', 'Super Mario Bros.', 'Tetris', 'Mario Kart Wii', 'Pokemon', 'Nintendo GS'],
            series: [
              [0.0064, -0.043, 0.156, 0.097, 0.098, 0.104, -0.039]
            ]
          }
        }
      }
    }
  }
</script>
<style>

</style>
