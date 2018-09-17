<template>
 <div class="vuestic-chat">
   <div class="chat-body" :style="{'height': height}" v-sticky-scroll="{animate: true, duration: 500}">
     <div class="chat-message" v-for="message in value.chatMessages" :class="{'yours': message.yours, 'alien': !message.yours}">
        {{message.text}}
     </div>
   </div>
   <div class="chat-controls" >
        <fieldset>
          <div class="form-group form-group-w-btn">
            <div class="input-group">
              <input @keypress="keyHandler($event)" v-model="inputMessage" required title=""/>
              <label class="control-label">Your message</label><i class="bar"></i>
            </div>
            <div class="btn btn-sm btn-primary" @click="sendMessage()">Send</div>
          </div>
        </fieldset>
   </div>
 </div>
</template>

<script>
  import StickyScroll from 'vuestic-directives/StickyScroll'
  import axios from 'axios'
  export default {
    name: 'vuestic-chat',

    directives: {StickyScroll},

    props: {
      value: {
        type: Array,
        default: []
      },
      height: {
        default: '30rem'
      }
    },

    data () {
      return {
        inputMessage: '',
        rollback: ''
      }
    },

    methods: {
      keyHandler (event) {
        if (event.keyCode === 13) {
          this.sendMessage()
        }
      },

      nlp (url, requestData) {
        return Promise.resolve(
          axios.post(url, requestData).then(function (res) {
            let result = {
              Speech: res.data['Speech'],
              Score: res.data['Score'],
              Intent: res.data['Intent']
            }
            if (result.Speech !== '') {
              return result
            } else {
              result.Intent = '-'
              result.Score = '-'
              result.Speech = ''
              res.data['Result'].forEach(function (e) {
                if (e['Source'] > result.Score) {
                  result.Intent = e['Intent']
                  result.Score = e['Source']
                  result.Speech = ''
                }
              })
              return result
            }
          }, function (error) {
            console.log(error)
          })
        )
      },

      sendMessage () {
        this.value.chatMessages.push({
          text: this.inputMessage,
          yours: true
        })
        if (this.inputMessage) {
          console.log(this.value.lang)
          let url = ''

          if (this.value.lang === 'cn') {
            console.log('cn')
            url = '/api/sub_agent'
            this.rollback = '抱歉,無法辨認'
          } else {
            console.log('en')
            url = '/api/sub_agent_en'
            this.rollback = "Sorry, can't detect"
          }

          //
          let requestData = {
            system_id: this.value.system_id,
            agent_id: this.value.agent_id,
            text: this.inputMessage
          }
          this.nlp(url, requestData).then((result) => {
            if (result['Speech'] !== '') {
              this.value.chatMessages.push({
                text: result.Speech,
                yours: false,
              })
              this.value.response.high_score_intent = result.Intent
              this.value.response.responses = result.Speech
              this.value.response.intent_score = result.Score
            } else {
              this.value.chatMessages.push({
                text: this.rollback,
                yours: false,
              })
              this.value.response.high_score_intent = result.Intent
              this.value.response.responses = '-'
              this.value.response.intent_score = result.Score
            }
          })
          this.inputMessage = ''
        }
      }
    },

    mounted () {
      this.$emit('input', this.value)
    }
  }
</script>

<style lang='scss' scoped>
  @import '../../../sass/_variables.scss';

  $chat-body-min-height: 18.75rem;
  $chat-body-mb: 1.5rem;
  $chat-message-mb: 0.625rem;
  $chat-message-py: 0.657rem;
  $chat-message-px: 1.375rem;
  $chat-message-br: 0.875rem;

  .vuestic-chat {
    width: 100%;
  }

  .chat-body {
    min-height: $chat-body-min-height;
    display: flex;
    flex-direction: column;
    margin-bottom: $chat-body-mb;
    overflow: auto;
  }

  .chat-message {
    padding: $chat-message-py $chat-message-px;
    margin-bottom: $chat-message-mb;
    border-radius: $chat-message-br;
    max-width: 70%;
    overflow-wrap: break-word;

    &:last-child {
      margin-bottom: 0;
    }

    &.alien {
      align-self: flex-start;
      border-top-left-radius: 0;
      background-color: $light-gray2;
    }

    &.yours {
      align-self: flex-end;
      border-top-right-radius: 0;
      background-color: $brand-primary;
    }

    .chat-message-input {
      resize: vertical !important;
    }
  }


</style>
