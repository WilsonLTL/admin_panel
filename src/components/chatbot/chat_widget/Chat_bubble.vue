<template>
  <div class="charts-page">
    <vuestic-widget class="chart-widget" :headerText="'Chatbot Widget'">

      <div class="row" style="margin: 10px;">
        <div class="col-md-4" style="height:400px;margin: 10px; border: #d2d5d8 solid .5px;">
          <button id="chat_button" style="width: 50%;background-color:transparent;margin: 10px;right: 0;border:none;">
            <img width="48" height="48" src="http://icons.iconarchive.com/icons/graphicloads/100-flat/256/home-icon.png"/>
          </button>

          <div id="chat_widget_display" style="border: #d2d5d8 solid .5px;width: 75%;max-width:200px;height: 300px;border-radius: 10px;margin: 0 auto ;box-shadow:2px 2px 1px 1px rgba(20%,20%,40%,0.5);">
            <div id="nav_header" style="width: 100%;height: 25px;border-bottom: #d2d5d8 solid .5px;">
              <button id="cross" style="width: 10%;height: 100%;margin :0 10px 0 10px;background-color: transparent;border: none;">
                <label>X</label>
              </button>
              <label id="nav_header_title">Chat with us</label>
            </div>
            <div id="chat" style="width: 100%;height: 275px;">
              <!--<div id="footer" style="position: absolute;bottom: 40px;">-->
                <!--<textarea style="border:solid 1px #d2d5d8;border-radius: 10px;margin: 0 0 0 5px;width: 60%;height: 35px;box-shadow:2px 2px 1px 1px rgba(20%,20%,40%,0.5);"></textarea>-->
                <!--<button style="background-image:url('https://png.icons8.com/ios/1600/sent.png');background-position: center;background-repeat: no-repeat;background-size: cover;margin: 0px 10px;background-color: transparent;border-radius: 10px;width: 20%;height: 40px;box-shadow: rgba(51, 51, 102, 0.5) 2px 2px 1px 1px;">-->
                  <!--&lt;!&ndash;<img width="24px" height="24px"  src="http://cdn.onlinewebfonts.com/svg/img_516624.png"/>&ndash;&gt;-->
                <!--</button>-->
              <!--</div>-->
            </div>
          </div>
        </div>

        <div class="col-md-3">
          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-nav-header" value="Chat with us" />
              <label class="control-label" for="input-nav-header">{{'forms.inputs.nav_header'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-background-image" value="https://image.freepik.com/free-psd/abstract-background-design_1297-87.jpg" />
              <label class="control-label" for="input-background-image">{{'forms.inputs.backgroundImage'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-send-button-image" value="https://png.icons8.com/ios/1600/sent.png" />
              <label class="control-label" for="input-send-button-image">{{'forms.inputs.send_button'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-widget-image" value="http://icons.iconarchive.com/icons/graphicloads/100-flat/256/home-icon.png" />
              <label class="control-label" for="input-widget-image">{{'forms.inputs.widget_image'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>
        </div>


        <div class="col-md-3">
          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-nav-header-color" value="transparent" />
              <label class="control-label" for="input-nav-header">{{'forms.inputs.nav_header_color'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-title-color" value="#34495e" />
              <label class="control-label" for="input-nav-header">{{'forms.inputs.nav_title_color'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-nav-border-color" value="#34495e" />
              <label class="control-label" for="input-nav-border-color">{{'forms.inputs.nav_border_color'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-background-color" value="transparent" />
              <label class="control-label" for="input-nav-header">{{'forms.inputs.background_color'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

          <div style="bottom: 0;" class="form-group form-group-w-btn">
            <div class="input-group">
              <input id="input-textarea-color" value="white" />
              <label class="control-label" for="input-nav-header">{{'forms.inputs.textAreaColor'
                | translate }}</label><i
              class="bar"></i>
            </div>
          </div>

        </div>
      </div>
      <button class="btn btn-primary btn-micro" v-on:click="download_chatbot_widget">
        <span aria-hidden="true" class="entypo entypo-download" style="font-size: 17px;"></span>
        {{'Export'}}
      </button>
    </vuestic-widget>
  </div>
</template>

<script>
  import JQuery from 'jquery'
  export default {
    name: 'Chat_bubble',
    data () {
      return {
        background_image_url: 'https://image.freepik.com/free-psd/abstract-background-design_1297-87.jpg',
        send_image_url: '',
        nav_header: 'Chat with us'
      }
    },
    mounted: function () {
      let $ = JQuery
      $(`#chat_button`).click(function () {
        $(`#chat_widget_display`).toggle('')
      })
      $(`#cross`).click(function () {
        $(`#chat_widget_display`).toggle('')
      })
    }
  }

</script>
<style scoped>

</style>
