<template>
  <div class="charts-page">

    <div style="margin-bottom: 30px;">
      <button class="btn btn-secondary btn-micro" v-on:click="add_agent">
        <span aria-hidden="true" class="entypo entypo-plus" style="font-size: 17px;"></span>
        {{'Add new agents'}}
      </button>
    </div>


    <vuestic-alert type="success" :withCloseBtn="true">
      <span class="badge badge-pill badge-success">{{'notificationsPage.alerts.success' | translate}}</span>
      {{'notificationsPage.alerts.successMessage' | translate}}
      <i class="fa fa-close alert-close"></i>
    </vuestic-alert>

    <div class="row">

      <div class="col-md-4" v-for="item in cn_result.agent">
        <vuestic-widget class="chart-widget" :headerText="'Agent Profile'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name=item.agent_name :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-primary btn-micro" v-on:click="edit_cn_agent(item)">
              <span aria-hidden="true" class="fa fa-edit">{{'Edit'}}</span>
            </button>
            <pre>&#9;</pre>
            <button class="btn btn-dark btn-micro" v-on:click="delete_agent(item)">
              <span aria-hidden="true" class="fa fa-trash">{{'Delete'}}</span>
            </button>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-4" v-for="item in en_result.agent">
        <vuestic-widget class="chart-widget" :headerText="'Agent Profile'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name=item.agent_name :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-primary btn-micro" v-on:click="edit_en_agent(item)">
              <span aria-hidden="true" class="fa fa-edit">{{'Edit'}}</span>
            </button>
            <pre>&#9;</pre>
            <button class="btn btn-dark btn-micro" v-on:click="delete_agent(item)">
              <span aria-hidden="true" class="fa fa-trash">{{'Delete'}}</span>
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
    name: 'users-members-tab',
    data () {
      return {
        cn_result: {
          system_id: 12312,
          agent: []
        },
        en_result: {
          system_id: 12312,
          agent: []
        }
      }
    },
    mounted: function () {
      let _this = this
      axios.post('/api/list_user_by_system_id', {'system_id': 12312}).then(function (res) {
        console.log(_this.cn_result)
        for (let key in res.data['result']) {
          console.log(res.data['result'][key])
          _this.cn_result.agent.push(res.data['result'][key])
        }
      }, function (error) {
        console.log(error)
      })
      axios.post('/api/list_user_by_system_id_en', {'system_id': 12312}).then(function (res) {
        console.log(_this.en_result)
        for (let key in res.data['result']) {
          console.log(res.data['result'][key])
          _this.en_result.agent.push(res.data['result'][key])
        }
      }, function (error) {
        console.log(error)
      })
    },
    methods: {
      add_agent: function () {
        let _this = this
        let name = window.prompt('Please enter a new agent name')
        if (name === null) {
          alert('Please enter a name!!')
        } else {
          let data = {
            'agent_id': 1290378912,
            'agent_name': name,
            'intents': []
          }
          let type = window.prompt('Please select chatbot type (chinese/english)')
          if (type === 'chinese') {
            _this.cn_result.agent.push(data)
            this.$router.push({name: 'edit_agent', params: {data: _this.cn_result, item: data, lang: 'cn'}})
          } else if (type === 'english') {
            _this.en_result.agent.push(data)
            this.$router.push({name: 'edit_agent', params: {data: _this.cn_result, item: data, lang: 'en'}})
          } else {
            alert('Please select a valid type')
          }
        }
      },
      edit_cn_agent: function (item) {
        let _this = this
        console.log(item)
        this.$router.push({name: 'edit_agent', params: {data: _this.cn_result, item: item, lang: 'cn'}})
      },
      edit_en_agent: function (item) {
        let _this = this
        console.log(item)
        this.$router.push({name: 'edit_agent', params: {data: _this.en_result, item: item, lang: 'en'}})
      },
      delete_agent: function (item) {
        if (confirm('Are you sure to delete this agent?')) {
          let index = this.items.indexOf(item)
          this.items.splice(index, 1)
        }
      }
    }
  }

</script>

<style lang="scss" scoped>
  .vuestic-profile-card {
    margin-left: 1rem;

    @include media-breakpoint-up(md) {
      margin-top: -$tab-content-pt;
    }

    @include media-breakpoint-down(md) {
      margin-bottom: $tab-content-pt;
      margin-left: 0;
    }
  }

  .widget.chart-widget {
    height:auto ;
  }

</style>
