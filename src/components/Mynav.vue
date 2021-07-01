<template>
  <nav>
    <v-app-bar app class="purple" dark dense>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer">
        <v-icon v-show="drawer==true">mdi-chevron-left</v-icon>
        <v-icon v-show="drawer==false">mdi-chevron-right</v-icon>
      </v-app-bar-nav-icon>

      <v-toolbar-title class="text-uppercase ">
        <span class="font-weight-light">My</span>
        <span class="font-weight-bold">Todo</span>
      </v-toolbar-title>
      <v-divider inset vertical class="ml-4"></v-divider>
      <span class=" ml-1 font-weight-thin">Enjoy with us </span>
      <v-spacer></v-spacer>

      <v-divider inset vertical class="mr-1"></v-divider>

      <v-menu  offset-y rounded="0" >
      <template v-slot:activator="{on,attrs}">
        <v-btn class="mr-1" text dark v-bind="attrs" v-on="on">
          Menu
          <v-icon>mdi-menu-down</v-icon>
        </v-btn>
        
      </template>

      <v-list >
        <v-list-item link v-for="link in items" :key="link.text" router :to="link.route">
          <v-list-item-title>{{link.text}}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
    <v-divider inset vertical  class="mr-1"></v-divider>

      <v-btn text>
        <span>LogIn </span>
        <v-icon right>mdi-login</v-icon>
      </v-btn>
    </v-app-bar>

    <!--  -->
    <!-- <v-navigation-drawer v-model="drawer" absolute floating temporary clipped> -->
    <v-navigation-drawer
      v-model="drawer"
      app
      dark
      class="purple"
    >
      <v-row class="flex-column text-center" >
        <v-col class="mt-10"  >
          <v-avatar size="90">
            <v-img src="/images/b.jpg"></v-img>
          </v-avatar>
        </v-col>
        <v-col>
          <p class="white--text subtitle-2 mb-0">Mohammed Alsir</p>
        </v-col>
        <v-col class="mt-0 mb-5">
          <Popup /> 
        </v-col>
      </v-row>
      <v-list nav dense>
        <!-- <v-subheader>Main</v-subheader> -->
        <v-list-item-group v-model="selectedItem" color="white">
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            router
            :to="item.route"
          >
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <!--  -->
  </nav>
</template>

<script>
import Popup from './Popup.vue'
export default {
  components:{Popup},
  data: () => ({
    clipped: false,
    drawer: false,
    group: null,
    selectedItem: 0,
    items: [
      { text: "Dashboard", icon: "mdi-clock", route: "/" },
      { text: "Project", icon: "mdi-account", route: "/project" },
      { text: "Team", icon: "mdi-flag", route: "/team" },
    ],
  }),
  watch: {
    group() {
      this.drawer = false;
    },
  },
};
</script>
