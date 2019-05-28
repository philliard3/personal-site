<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md8>
      <v-container>
        <v-layout row wrap>
          <v-flex xs12>
            <v-card>
              <v-card-title
                class="display-2 font-weight-light"
                primary-title
              >Email &amp; Social Media</v-card-title>
              <v-card-text>
                <v-list one-line>
                  <template v-for="(link, l) in links">
                    <v-divider v-if="link.divider" :key="l" :inset="link.inset"></v-divider>

                    <v-list-tile v-else :key="link.title" avatar :href="link.to">
                      <v-list-tile-avatar>
                        <img v-if="link.logo" :src="link.logo">
                        <v-icon v-else color="black">{{ link.icon }}</v-icon>
                      </v-list-tile-avatar>
                      <v-list-tile-content>
                        <v-list-tile-title v-html="link.title"></v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                  </template>
                </v-list>
              </v-card-text>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          title: "GitHub",
          to: "https://github.com/philliard3",
          color: "black",
          textColor: "white",
          logo:
            "https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png"
        },
        { divider: true, inset: true },
        {
          title: "LinkedIn",
          to: "https://www.linkedin.com/in/phillip-hilliard-994235bb/",
          logo:
            "https://upload.wikimedia.org/wikipedia/commons/c/ca/LinkedIn_logo_initials.png"
        },
        { divider: true, inset: true },
        {
          title: "Twitter",
          to: "https://twitter.com/philliardcode",
          logo:
            "https://www.seas.upenn.edu/~pdh/Twitter_Social_Icon_Circle_Color.png"
        },
        { divider: true, inset: true },
        {
          title: "Research Email",
          to: "mailto:pdh@seas.upenn.edu",
          icon: "contact_mail"
        },
        { divider: true, inset: true },
        {
          title: "Professional Email",
          to: "mailto:pdhilliard3@gmail.com",
          icon: "contact_mail"
        }
      ]
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
