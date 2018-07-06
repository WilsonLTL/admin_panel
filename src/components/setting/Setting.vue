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

      <vuestic-widget class="chart-widget" :headerText="'API Configuration Setting'">
        <div class="form-group">
          <div class="input-group">
            <input id="simple-input" value="http://ec2-13-229-73-34.ap-southeast-1.compute.amazonaws.com:5000" required/>
            <label class="control-label" for="simple-input">API URL</label><i class="bar"></i>
            <small class="help text-secondary">
              The api url of the system, please make sure the link is valid before modify the link, and press 'Update' to confirm
              the modification. <br >
              Example: Http://DOMAIN_NAME:PORT_NUMBER
            </small>
          </div>
        </div>
        <button class="btn btn-primary btn-micro" v-on:click="back_page">
          <span aria-hidden="true" class="glyphicon glyphicon-ok" style="font-size: 17px;"></span>
          {{'Update'}}
        </button>
      </vuestic-widget>


    </div>
    <div class="col-md-4">
      <vuestic-widget class="chart-widget" :headerText="'User Profile'">
        <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
          <vuestic-profile-card :name="asdasd" :location="'172.9.0.124'" photoSource="https://i.imgur.com/2CmhHsQ.png"
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
  export default {
    name: 'Setting',
    data () {
      return {
        isMale: true
      }
    }
  }
</script>

<style scoped>

</style>
