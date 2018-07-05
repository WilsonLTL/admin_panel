<template>
  <div class="charts-page">

    <div style="margin-bottom: 30px;">
      <button class="btn btn-secondary btn-micro">
        <span aria-hidden="true" class="entypo entypo-plus" style="font-size: 17px;"></span>
        {{'Add new kits'}}
      </button>
    </div>

    <vuestic-alert type="success" :withCloseBtn="true">
      <span class="badge badge-pill badge-success">{{'notificationsPage.alerts.success' | translate}}</span>
      {{'notificationsPage.alerts.successMessage' | translate}}
      <i class="fa fa-close alert-close"></i>
    </vuestic-alert>

    <div class="row">

      <div class="col-md-4">
        <vuestic-widget class="chart-widget" :headerText="'Agent_name'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="'Veronique Lee'" :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-dark btn-micro">
              <span aria-hidden="true" class="iconicstroke iconicstroke-link" style="font-size: 15px;"></span>
              {{'Disconnect'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-4">
        <vuestic-widget class="chart-widget" :headerText="'Agent_name'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="'Veronique Lee'" :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-dark btn-micro">
              <span aria-hidden="true" class="iconicstroke iconicstroke-link" style="font-size: 15px;"></span>
              {{'Disconnect'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-4">
        <vuestic-widget class="chart-widget" :headerText="'Agent_name'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="'Veronique Lee'" :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-dark btn-micro">
              <span aria-hidden="true" class="iconicstroke iconicstroke-link" style="font-size: 15px;"></span>
              {{'Disconnect'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-4">
        <vuestic-widget class="chart-widget" :headerText="'Agent_name'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="'Veronique Lee'" :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-dark btn-micro">
              <span aria-hidden="true" class="iconicstroke iconicstroke-link" style="font-size: 15px;"></span>
              {{'Disconnect'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-4">
        <vuestic-widget class="chart-widget" :headerText="'Agent_name'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="'Veronique Lee'" :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-dark btn-micro">
              <span aria-hidden="true" class="iconicstroke iconicstroke-link" style="font-size: 15px;"></span>
              {{'Disconnect'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

      <div class="col-md-4">
        <vuestic-widget class="chart-widget" :headerText="'Agent_name'">
          <div class="d-flex justify-content-center align-items-center" style="margin-top: 30px">
            <vuestic-profile-card :name="'Veronique Lee'" :location="'172.9.0.124'" photoSource="http://i.imgur.com/NLrdqsk.png"
                                  :social="{}">
            </vuestic-profile-card>
          </div>
          <div class="d-flex justify-content-center align-items-center">
            <button class="btn btn-dark btn-micro">
              <span aria-hidden="true" class="iconicstroke iconicstroke-link" style="font-size: 15px;"></span>
              {{'Disconnect'}}
            </button>
          </div>
        </vuestic-widget>
      </div>

    </div>
  </div>


</template>

<script>
  import LineChartData from 'data/charts/LineChartData'
  import BubbleChartData from 'data/charts/BubbleChartData'
  import PieChartData from 'data/charts/PieChartData'
  import DonutChartData from 'data/charts/DonutChartData'
  import VerticalBarChartData from 'data/charts/VerticalBarChartData'
  import HorizontalBarChartData from 'data/charts/HorizontalBarChartData'
  export default {
    name: 'users-members-tab',

    data () {
      return {
        bubbleChartData: BubbleChartData,
        lineChartData: LineChartData,
        pieChartData: PieChartData,
        donutChartData: DonutChartData,
        verticalBarChartData: VerticalBarChartData,
        horizontalBarChartData: HorizontalBarChartData
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
