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

    <vuestic-alert id="success" type="success" :withCloseBtn="true" hidden>
      <span class="badge badge-pill badge-success">Success</span>
      Agent detail update successful
      <i class="fa fa-close alert-close"></i>
    </vuestic-alert>
    <vuestic-alert id="info" type="info" :withCloseBtn="true" hidden>
      <span class="badge badge-pill badge-info">{{'notificationsPage.alerts.info' | translate}}</span>
      {{'notificationsPage.alerts.infoMessage' | translate}}
    </vuestic-alert>
    <vuestic-alert id="warning" type="warning" :withCloseBtn="true" hidden>
      <span class="badge badge-pill badge-warning">Processing</span>
      Agent detail updating, please wait and don't exist the bower
    </vuestic-alert>
    <vuestic-alert id="danger" type="danger" :withCloseBtn="true" hidden>
      <span class="badge badge-pill badge-danger">Fail</span>
      Agent detail update fail
    </vuestic-alert>

    <div class="row">
      <div class="col-md-8">
        <div class="row">
          <div class="col-md-12">
            <vuestic-widget class="chart-widget" :headerText="'Agent Profile'">
              <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
                <vuestic-profile-card :name="agent_name" :cation="'172.9.0.124'" photoSource="https://i.imgur.com/2CmhHsQ.png"
                                      :social="{}">
                </vuestic-profile-card>
              </div>
              <button class="btn btn-primary btn-micro" v-on:click="edit_agent_name">
                <span aria-hidden="true" class="fa fa-edit" style="font-size: 17px;"></span>
                {{'Edit agent name'}}
              </button>
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
                <button class="col-md-6 btn btn-primary btn-micro" style="margin-top:7px;border-bottom-right-radius: 5px;border-top-right-radius: 5px;" v-on:click="edit_intent(item)">
                  <span aria-hidden="true" class="fa fa-edit"></span>
                  Edit
                </button>
                <button class="col-md-6 btn btn-dark btn-micro" style="margin-top:7px;border-bottom-left-radius: 5px;border-top-left-radius: 5px;" v-on:click="delete_intent(item)">
                  <span aria-hidden="true" class="fa fa-trash" ></span>
                  Dele
                </button>
              </div>
            </vuestic-widget>
          </div>
        </div>
      </div>

      <div class="col-md-4">
        <vuestic-widget v-model="message.response" class="chart-widget" :headerText="'Debug Message'">
          <u>Highest Score Intent:</u>
          <p id="detect_intent_name">{{message.response.high_score_intent}}</p>
          <u>Responses:</u>
          <p id="system_response">{{message.response.responses}}</p>
          <u>Threshold:</u><br>
          <p id="threshold_score">{{message.response.threshold}}</p>
          <u>Score:</u><br>
          <p id="intent_score">{{message.response.intent_score}}</p>
        </vuestic-widget>
        <vuestic-widget class="chart-widget" :headerText="'Agent Chat'">
          <vuestic-chat v-model="message"></vuestic-chat>
        </vuestic-widget>
      </div>
    </div>

  </div>


</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Edit_agent',
    value: [],
    data () {
      console.log('item', this.$route.params.item)
      console.log('data', this.$route.params.data)
      return {
        agent_name: this.$route.params.item['agent_name'],
        items: this.$route.params.item['intents'],
        item: this.$route.params.item,
        data: this.$route.params.data,
        lang: this.$route.params.lang,

        message: {
          system_id: this.$route.params.data['system_id'],
          agent_id: this.$route.params.item['agent_id'],
          lang: this.$route.params.lang,
          response: {
            high_score_intent: '-',
            responses: '-',
            threshold: 0.6,
            intent_score: '-'
          },
          chatMessages: []
        }
      }
    },
    mounted: function () {
      let _this = this
      let successmsg = document.getElementById('success')
      // let infomsg = document.getElementById('info')
      let warningmsg = document.getElementById('warning')
      let dangermsg = document.getElementById('danger')

      console.log('data:', this.$route.params.data['system_id'])
      let url = ''
      if (_this.lang === 'cn') {
        url = '/api/update_agent'
        this.message.chatMessages.push({text: '測試系統正常,請輸入.', yours: false})
      } else {
        url = '/api/update_agent_en'
        this.message.chatMessages.push({text: 'Testing system start, please enter.', yours: false})
      }
      warningmsg.hidden = false
      axios.post(url, _this.data).then(function (res) {
        console.log(res.data)
        warningmsg.hidden = true
        successmsg.hidden = false
      }, function (error) {
        warningmsg.hidden = true
        dangermsg.hidden = false
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
        let record = window.prompt('Please enter a new intent name:')
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
      },
      edit_agent_name: function () {
        let _this = this
        let url = ''
        let name = window.prompt('Please enter a new agent name:')
        if (name !== null) {
          _this.item['agent_name'] = name
          _this.agent_name = name
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
        } else {
          alert('Please enter a valid name!')
        }
      }
    }
  }

</script>

<style scoped>

</style>
