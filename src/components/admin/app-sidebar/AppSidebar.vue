<template>
  <vuestic-sidebar :hidden="this.isOpen"
                   :toggleWithoutAnimation="toggleWithoutAnimation">
    <template slot="menu">
      <sidebar-link
        :to="{ name: 'dashboard' }">
        <span slot="title">
          <span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-dashboard"></span>
          <span>{{ $t('menu.dashboard') }}</span>
        </span>
      </sidebar-link>
      <!--<sidebar-link-group>-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-statistics"></span>-->
          <!--<span>{{ $t('menu.statistics') }}</span>-->
        <!--</span>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'charts' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.charts') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'progress-bars' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.progressBars') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
      <!--</sidebar-link-group>-->
      <!--<sidebar-link-group>-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-forms"></span>-->
          <!--<span>{{ $t('menu.forms') }}</span>-->
        <!--</span>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'form-elements' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.formElements') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'form-wizard' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.formWizards') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'medium-editor' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.mediumEditor') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
      <!--</sidebar-link-group>-->
      <!--<sidebar-link-->
        <!--:to="{ name: 'tables' }">-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-tables"></span>-->
          <!--<span>{{ $t('menu.tables') }}</span>-->
        <!--</span>-->
      <!--</sidebar-link>-->
      <!--<sidebar-link-group>-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-ui-elements"></span>-->
          <!--<span>{{ $t('menu.uiElements') }}</span>-->
        <!--</span>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'typography' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.typography') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'buttons' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.buttons') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'notifications' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.notifications') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'icons' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.icons') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'spinners' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.spinners') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'grid' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.grid') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'modals' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.modals') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'tree-view' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.treeView') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
      <!--</sidebar-link-group>-->
      <!--<sidebar-link-->
        <!--:to="{ name: 'extra' }">-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-extras"></span>-->
          <!--<span>{{ $t('menu.extra') }}</span>-->
        <!--</span>-->
      <!--</sidebar-link>-->
      <!--<sidebar-link-group>-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-auth"></span>-->
          <!--<span>{{ $t('menu.auth') }}</span>-->
        <!--</span>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'login' }"-->
          <!--target="_blank"-->
          <!--:isChildLink="true">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.login') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'signup' }"-->
          <!--target="_blank">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('menu.signUp') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
      <!--</sidebar-link-group>-->
      <!--<sidebar-link-group>-->
        <!--<span slot="title">-->
          <!--<span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-maps"></span>-->
          <!--<span>{{ $t('menu.maps') }}</span>-->
        <!--</span>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'google-maps' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ 'Google Maps' }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'yandex-maps' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ 'Yandex Maps' }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'leaflet-maps' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ 'Leaflet Maps' }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'bubble-maps' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('Bubble Maps') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
        <!--<sidebar-link-->
          <!--:to="{ name: 'line-maps' }">-->
          <!--<span slot="title">-->
            <!--<span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>-->
            <!--<span>{{ $t('Line Maps') }}</span>-->
          <!--</span>-->
        <!--</sidebar-link>-->
      <!--</sidebar-link-group>-->
      <sidebar-link-group>
        <span slot="title">
          <span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-user"></span>
          <span>{{ $t('menu.chatbot') }}</span>
        </span>
        <sidebar-link
          :to="{ name: 'agents' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.agents') }}</span>
          </span>
        </sidebar-link>
        <sidebar-link
          :to="{ name: 'voice_kits' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.voice_kits') }}</span>
          </span>
        </sidebar-link>
        <sidebar-link
          :to="{ name: 'chat_widget' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.chat_widget') }}</span>
          </span>
        </sidebar-link>
        <sidebar-link
          :to="{ name: 'chat_widget' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.sentiment_analysis') }}</span>
          </span>
        </sidebar-link>
        <sidebar-link
          :to="{ name: 'chat_widget' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.paragraph_classification') }}</span>
          </span>
        </sidebar-link>
      </sidebar-link-group>
      <sidebar-link-group>
        <span slot="title">
          <span class="sidebar-menu-item-icon entypo entypo-eye"></span>
          <span>{{ $t('menu.vision') }}</span>
        </span>
        <sidebar-link
          :to="{ name: 'user' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.user') }}</span>
          </span>
        </sidebar-link>
        <sidebar-link
          :to="{ name: 'vision_kits' }">
          <span slot="title">
            <span class="sidebar-menu-item-icon vuestic-icon fa fa-circle-o"></span>
            <span>{{ $t('menu.vision_kit') }}</span>
          </span>
        </sidebar-link>
      </sidebar-link-group>
      <sidebar-link
      :to="{ name: 'setting' }">
      <span slot="title">
      <span class="sidebar-menu-item-icon vuestic-icon vuestic-icon-settings"></span>
      <span>{{ $t('menu.setting') }}</span>
      </span>
      </sidebar-link>
    </template>
  </vuestic-sidebar>
</template>

<script>

  import VuesticSidebar from '../../../vuestic-theme/vuestic-components/vuestic-sidebar/VuesticSidebar'
  import {mapGetters} from 'vuex'
  import SidebarLink from './components/SidebarLink'
  import SidebarLinkGroup from './components/SidebarLinkGroup'

  export default {
    name: 'app-sidebar',
    components: {
      VuesticSidebar,
      SidebarLink,
      SidebarLinkGroup
    },
    props: {
      isOpen: {
        type: Boolean,
        required: true
      }
    },
    computed: {
      ...mapGetters([
        'toggleWithoutAnimation'
      ]),
    }
  }


</script>
