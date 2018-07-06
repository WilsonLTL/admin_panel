<template>
  <div class="charts-page">

    <div style="margin-bottom: 30px;">
      <button class="btn btn-secondary btn-micro" v-on:click="back_page()">
        <span aria-hidden="true" class="entypo entypo-back" style="font-size: 17px;"></span>
        {{'Back'}}
      </button>
    </div>

    <vuestic-alert type="success" :withCloseBtn="true">
      <span class="badge badge-pill badge-success">{{'notificationsPage.alerts.success' | translate}}</span>
      {{'notificationsPage.alerts.successMessage' | translate}}
      <i class="fa fa-close alert-close"></i>
    </vuestic-alert>

    <div class="row">

      <div class="col-md-12">
        <vuestic-widget class="chart-widget" :headerText=intent_name>
          <h3><u>Training phrases :</u></h3>
          <table  class="table first-td-padding">
            <tbody>
              <tr v-for="phrase in training_phrases">
                <td>{{phrase}}</td>
                <td>
                  <button class="btn btn-pale btn-micro" v-on:click="delete_phrase(phrase)">
                    <span aria-hidden="true" class="fa fa-trash" ></span>
                    Delete
                  </button>
                </td>
              </tr>

              <tr>
                <td>
                  <button id="new_phrases" class="btn btn-primary btn-micro" v-on:click="add_new_phrases">
                    <span aria-hidden="true" class="entypo entypo-plus" style="font-size: 17px;"></span>
                    {{'Add new phrases'}}
                  </button>
                </td>
              </tr>
            </tbody>
          </table>


          <h3><u>Response Text :</u></h3>
          <table class="table first-td-padding">
            <tbody>
            <tr v-for="text in response_text">
              <td>{{text}}</td>
              <td>
                <button class="btn btn-pale btn-micro" v-on:click="delete_text(text)">
                  <span aria-hidden="true" class="fa fa-trash" ></span>
                  Delete
                </button>
              </td>
            </tr>

            <tr>
              <td>
                <button id="new_text" class="btn btn-primary btn-micro" v-on:click="add_new_text">
                  <span aria-hidden="true" class="entypo entypo-plus" style="font-size: 17px;"></span>
                  {{'Add new text'}}
                </button>
              </td>
            </tr>
            </tbody>
          </table>

          <div class="row">
            <button class="col-md-12 btn btn-primary btn-micro" v-on:click="submit_update">
              <span aria-hidden="true" class="glyphicon glyphicon-ok"></span>
              {{'Submit'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

    </div>
  </div>


</template>


<script>

  export default {
    name: 'Modify_intent',
    data () {
      return {
        intent_name: 'Intent name: ' + this.$route.params.item['intent_name'],
        response_text: [],
        training_phrases: [],
        items: this.$route.params.items,
        item: this.$route.params.item,
        data: this.$route.params.data
      }
    },
    mounted: function () {
      let _this = this
      for (let key in this.$route.params.item['training_phrases']) {
        _this.training_phrases.push(this.$route.params.item['training_phrases'][key])
      }
      for (let key in this.$route.params.item['response_text']) {
        _this.response_text.push(this.$route.params.item['response_text'][key])
      }
    },
    methods: {
      add_new_phrases: function () {
        let _this = this
        if (event) {
          let record = window.prompt('Please enter a new phrase', '')
          if (record === null || record === '') {
            alert('Please enter a valid sentence!')
          } else {
            _this.training_phrases.push(record)
          }
        }
      },
      add_new_text: function () {
        let _this = this
        if (event) {
          let record = window.prompt('Please enter a new phrase', '')
          if (record === null || record === '') {
            alert('Please enter a valid sentence!')
          } else {
            _this.response_text.push(record)
          }
        }
      },
      delete_phrase: function (row) {
        let _this = this
        let index = _this.training_phrases.indexOf(row)
        _this.training_phrases.splice(index, 1)
      },
      delete_text: function (row) {
        let _this = this
        let index = _this.response_text.indexOf(row)
        _this.response_text.splice(index, 1)
      },
      back_page: function () {
        this.$router.push({name: 'edit_agent', params: {data: this.$route.params.data, item: this.$route.params.items, lang: this.$route.params.lang}})
      },
      submit_update: function () {
        let _this = this
        this.$route.params.item['training_phrases'] = _this.training_phrases
        this.$route.params.item['response_text'] = _this.response_text
        this.$router.push({name: 'edit_agent', params: {data: this.$route.params.data, item: this.$route.params.items, lang: this.$route.params.lang}})
      }
    }
  }

</script>


<style scoped>

</style>

