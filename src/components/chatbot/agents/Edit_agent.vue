<template>
  <div class="charts-page">

    <div style="margin-bottom: 30px;">
      <button class="btn btn-secondary btn-micro" v-on:click="back_page">
        <span aria-hidden="true" class="entypo entypo-back" style="font-size: 17px;"></span>
        {{'Back'}}
      </button>
      <button class="btn btn-secondary btn-micro" v-on:click="add_intent">
        <span aria-hidden="true" class="entypo entypo-plus" style="font-size: 17px;"></span>
        {{'Add a new intent'}}
      </button>
    </div>


    <vuestic-alert type="success" :withCloseBtn="true">
      <span class="badge badge-pill badge-success">{{'notificationsPage.alerts.success' | translate}}</span>
      {{'notificationsPage.alerts.successMessage' | translate}}
      <i class="fa fa-close alert-close"></i>
    </vuestic-alert>

    <div class="row">

      <div class="col-md-12">
        <vuestic-widget class="chart-widget" :headerText="'Agent Profile'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="agent_name" :cation="'172.9.0.124'" photoSource="https://i.imgur.com/2CmhHsQ.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-6" v-for="item in items">
        <vuestic-widget class="chart-widget" :headerText="item.intent_name">
          <h5>Training pharses :</h5>
          <div id="form_content_1_training_pharses" class="d-flex">
            <ol>
              <li v-for="phrases in item.training_phrases">{{phrases}}</li>
            </ol>
          </div>

          <h5>Response Text :</h5>
          <div id="form_content_1_response_text"class="d-flex">
            <ol>
              <li v-for="response_text in item.response_text">{{response_text}}</li>
            </ol>
          </div>

          <div class="row">
            <button class="col-md-6 btn btn-primary btn-micro" v-on:click="edit_intent(item)">
              <span aria-hidden="true" class="fa fa-edit"></span>
              Edit
            </button>
            <button class="col-md-6 btn btn-pale btn-micro" v-on:click="delete_intent(item)">
              <span aria-hidden="true" class="fa fa-trash" ></span>
              Delete
            </button>
          </div>
        </vuestic-widget>
      </div>
    </div>
  </div>


</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Edit_agent',
    data () {
      console.log(this.$route.params.data)
      return {
        agent_name: this.$route.params.item['agent_name'],
        items: this.$route.params.item['intents'],
        data: this.$route.params.data,
        lang: this.$route.params.lang
      }
    },
    mounted: function () {
      let _this = this
      let url = ''
      if (_this.lang === 'cn') {
        url = '/api/update_agent'
      } else {
        url = '/api/update_agent_en'
      }
      axios.post(url, _this.data).then(function (res) {
        console.log(res.data)
      }, function (error) {
        console.log(error)
      })
    },
    methods: {
      delete_intent: function (row) {
        if (confirm('Are you sure to delete this intent?')) {
          let index = this.items.indexOf(row)
          this.items.splice(index, 1)

          let _this = this
          let url = ''
          if (_this.lang === 'cn') {
            url = '/api/update_agent'
          } else {
            url = '/api/update_agent_en'
          }
          axios.post(url, _this.data).then(function (res) {
            console.log(res.data)
          }, function (error) {
            console.log(error)
          })
        }
      },
      edit_intent: function (row) {
        let _this = this
        console.log('row:', row)
        console.log('data:', this.$route.params.data)
        this.$router.push({name: 'modify_intent', params: {items: this.$route.params.item, item: row, data: this.$route.params.data, lang: _this.lang}})
      },
      back_page: function () {
        this.$router.push({name: 'agents'})
      },
      add_intent: function () {
        let _this = this
        let record = window.prompt('Please enter a new intent name')
        if (record === null) {
          alert('Please enter a name!!')
        } else {
          let intent = {
            'intent_name': record,
            'response_text': [],
            'training_phrases': []
          }
          _this.items.push(intent)
          this.$router.push({name: 'modify_intent', params: {items: this.$route.params.item, item: intent, data: this.$route.params.data, lang: _this.lang}})
        }
      }
    }
  }
</script>

<style scoped>

</style>
