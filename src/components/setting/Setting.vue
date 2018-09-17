<template>
  <div class="charts-page">
    <div class="row">
    <div class="col-md-8">

        <div style="margin-bottom: 30px;">
          <button class="btn btn-secondary btn-micro" v-on:click="back_page">
            <span aria-hidden="true" class="entypo entypo-back" style="font-size: 17px;"></span>
            {{'Back'}}
          </button>
        </div>

      <vuestic-widget class="chart-widget" :headerText="'Agent API Configuration Setting'">
        <div class="form-group">
          <div class="input-group">
            <input id="agent_api_value" value="http://ec2-13-229-73-34.ap-southeast-1.compute.amazonaws.com:5000" required/>
            <label class="control-label" for="api_value">Agent API URL</label><i class="bar"></i>
            <small class="help text-secondary">
              The api url of the system, please make sure the link is valid before modify the link, and press 'Update' to confirm
              the modification. <br >
              Example: Http://DOMAIN_NAME:PORT_NUMBER
            </small>
          </div>
        </div>
        <button class="btn btn-primary btn-micro" v-on:click="update_api">
          <span aria-hidden="true" class="glyphicon glyphicon-ok" style="font-size: 17px;"></span>
          {{'Update'}}
        </button>
      </vuestic-widget>

      <vuestic-widget class="chart-widget" :headerText="'Twilio Configuration Setting'">
        <div class="form-group">
          <div class="row">
            <div class="input-group" style="margin:0px 0px 20px 0px;">
              <input id="twilio_sid_value" value="ACb53b98fdb036d61049759266232ed8e4" required/>
              <label class="control-label" for="twilio_sid_value">TWILIO SID</label><i class="bar"></i>
              <small class="help text-secondary">
                The sid of the system, please make sure the link is valid before modify the link, and press 'Update' to confirm
                the modification. <br >
                Example: BHJUFUTDYURFYIGUKJB
              </small>
            </div>
            <div class="input-group">
              <input id="twilio_token_value" value="c11f1ad436b88c40788cdc24a6fcbcc3" required/>
              <label class="control-label" for="twilio_token_value">TWILIO TOKEN</label><i class="bar"></i>
              <small class="help text-secondary">
                The access token of the system, please make sure the link is valid before modify the link, and press 'Update' to confirm
                the modification. <br >
                Example: jknfiahoicu02ucpnfoiunocfieoifja
              </small>
            </div>
          </div>
        </div>
        <button class="btn btn-primary btn-micro" v-on:click="update_api">
          <span aria-hidden="true" class="glyphicon glyphicon-ok" style="font-size: 17px;"></span>
          {{'Update'}}
        </button>
      </vuestic-widget>

      <vuestic-widget class="chart-widget" :headerText="'Chatbot Widget'">
        <div class="form-group">
          <div class="input-group">
            <small class="help text-secondary">
               Export the source code of the front end chatbot widget in your front end website<br >
               Enter the access token to check permission<br >
               For more detail, please follow the instruction in "README.md"
            </small>
          </div>
        </div>
        <button class="btn btn-primary btn-micro" v-on:click="download_chatbot_widget">
          <span aria-hidden="true" class="entypo entypo-download" style="font-size: 17px;"></span>
          {{'Export'}}
        </button>
      </vuestic-widget>

    </div>
    <div class="col-md-4">
      <vuestic-widget class="chart-widget" :headerText="'User Profile'">
        <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
          <vuestic-profile-card :name="'name'" :location="'172.9.0.124'" photoSource="https://i.imgur.com/2CmhHsQ.png"
                                :social="{}">
          </vuestic-profile-card>
        </div>
        <div style="margin: 30px">
          <h6 class="d-flex justify-content-center align-items-center">User Name:</h6>
          <h6 class="d-flex justify-content-center align-items-center">username</h6>
        </div>

        <div style="margin: 30px">
          <h6 class="d-flex justify-content-center align-items-center">User Gender:</h6>
          <fieldset>
            <vuestic-switch v-model="isMale">
              <span slot="trueTitle">{{'forms.controls.male' | translate}}</span>
              <span slot="falseTitle">{{'forms.controls.female' | translate}}</span>
            </vuestic-switch>
          </fieldset>
        </div>

        <div style="margin: 30px">
          <h6 class="d-flex justify-content-center align-items-center">Email Address:</h6>
          <h6 class="d-flex justify-content-center align-items-center">wilson12345@gmail.com</h6>
        </div>

        <div style="margin: 30px">
          <h6 class="d-flex justify-content-center align-items-center">Phone Number:</h6>
          <h6 class="d-flex justify-content-center align-items-center">+852 1234 5678</h6>
        </div>

        <div class="d-flex justify-content-center align-items-center">
          <button class="btn btn-primary btn-micro" v-on:click="edit_cn_agent(item)">
            <span aria-hidden="true" class="fa fa-edit">{{'Edit'}}</span>
          </button>
        </div>
      </vuestic-widget>
    </div>
  </div>
  </div>
</template>

<script>
  // let filename = '../../../config/config.json'
  // let data = require(filename)
  // let fs = require('fs')
  // import axios from 'axios'
  export default {
    name: 'Setting',
    data () {
      return {
        isMale: true
      }
    },
    methods: {
      back_page: function () {
        window.history.back()
      },
      // update_api: function () {
      //   let item = document.getElementById('api_value')
      //   console.log('data:', data)
      //   console.log('item:', item.value)
      //   data['api_url'] = item.value.toString()
      //   console.log('After:', data)
      //   let new_data = fs.readFileSync(filename)
      //   console.log(new_data)
      // },
      // download_chatbot_widget: function () {
      //   axios.post().then(function (data) {
      //     console.log('request code file')
      //   })
      // },
    }
  }
</script>

<style scoped>

</style>
