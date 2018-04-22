<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <card>
            <template slot="header">
              <h4 class="card-title">List of Machine Learning Algorithms</h4>
              <p class="card-category">With names of datasets on which they're applied</p>
            </template>
            <div class="table-responsive">
              <l-table class="table-hover table-striped"
                       :columns="table1.columns"
                       :data="table1.data">
              </l-table>
            </div>
          </card>

        </div>

        <div class="col-12">
          <card>
            <template slot="header">
              <h4 class="card-title">List of Opinion Mining Algorithms</h4>
              <p class="card-category">Also the List of Libraries used</p>
            </template>
            <div class="table-responsive">
              <l-table class="table-hove table-stripedr"
                       :columns="table2.columns"
                       :data="table2.data">
              </l-table>
            </div>
          </card>
        </div>

      </div>
    </div>
  </div>
</template>
<script>
  import LTable from 'src/components/UIComponents/Table.vue'
  import Card from 'src/components/UIComponents/Cards/Card.vue'
  const tableColumns = ['Id', 'Dataset', 'Algorithm']
  const tableData = [{
    id: 1,
    dataset: 'Video Game Sales',
    algorithm: 'Random Forest Regressor'
  },
  {
    id: 2,
    dataset: 'Video Game Sales',
    algorithm: 'Decision Tree Regressor'
  },
  {
    id: 3,
    dataset: 'Lead+Magnates',
    algorithm: 'Decision Tree Classifier'
  },
  {
    id: 4,
    dataset: 'Social_Network_Ads',
    algorithm: 'SVM'
  },
  {
    id: 5,
    dataset: 'Social_Network_Ads',
    algorithm: 'Logistic Regression'
  },
  {
    id: 6,
    dataset: 'Salary_Data',
    algorithm: 'Linear Regression'
  }]
  const tableColumns2 = ['Id', 'Method', 'Algorithm_Library']
  const tableData2 = [{
    id: 1,
    method: 'Naive Bayes',
    algorithm_library: 'Algorithm'
  },
  {
    id: 2,
    method: 'Bernoulli',
    algorithm_library: 'Algorithm'
  },
  {
    id: 3,
    method: 'Multinomial Bernoulli',
    algorithm_library: 'Algorithm'
  },
  {
    id: 4,
    method: 'NLTK',
    algorithm_library: 'Library'
  },
  {
    id: 5,
    method: 'Textblob',
    algorithm_library: 'Library'
  }]
  export default {
    components: {
      LTable,
      Card
    },
    data () {
      return {
        table1: {
          columns: [...tableColumns],
          data: [...tableData]
        },
        table2: {
          columns: [...tableColumns2],
          data: [...tableData2]
        }
      }
    }
  }
</script>
<style>
</style>
