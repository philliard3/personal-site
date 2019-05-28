<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" :clipped="clipped" fixed app>
      <v-list>
        <v-list-tile v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"/>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar :clipped-left="clipped" dark fixed app>
      <v-icon @click="drawer = !drawer">menu</v-icon>
      <nuxt-link to="/" class="no-underline">
        <v-toolbar-title class="font-weight-black" v-text="title"/>
      </nuxt-link>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt/>
      </v-container>
    </v-content>
    <v-footer :fixed="fixed" dark app>
      <v-layout>
        <v-flex 10 xs12 sm/>
        <v-flex xs12 sm2>
          <nuxt-link to="/social" class="no-underline">
            <span class="text-xs-center">Contact &nbsp;</span>
          </nuxt-link>
          <span class="text-xs-right">Phillip Hilliard &copy; 2019</span>
        </v-flex>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: true,
      fixed: true,
      items: [
        {
          icon: "home",
          title: "Home",
          to: "/"
        },
        {
          icon: "account_circle",
          title: "About",
          to: "/about"
        },
        {
          icon: "apps",
          title: "Projects",
          to: "/projects"
        },
        {
          icon: "share",
          title: "Links",
          to: "/social"
        }
      ],
      miniVariant: false,
      title: "Phillip Hilliard"
    };
  }
};
</script>

<style>
.no-underline {
  text-decoration: none;
  margin-left: 2%;
}
</style>

