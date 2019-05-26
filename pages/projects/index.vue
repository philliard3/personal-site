<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md8>
      <v-container>
        <v-layout>
          <v-flex xs12 sm4 flat>
            <v-text-field prepend-icon="search" label="Search term" v-model="searchTerm" clearable></v-text-field>
          </v-flex>
        </v-layout>
        <v-container fluid grid-list-xl>
          <v-layout row wrap>
            <v-flex xs12 v-if="filteredItems.length <= 0">
              <span class="headline">No results found</span>
            </v-flex>
            <v-flex v-else xs12 v-for="(item, i) in filteredItems" :key="i">
              <v-card
                :color="item.colors ? item.colors.color : cardColors[i%cardColors.length].color"
                :class="item.colors ? item.colors.class : cardColors[i%cardColors.length].class"
              >
                <v-card-title primary-title v-html="item.description"/>
                <v-card-text>
                  <v-chip
                    v-for="(tag, t) in item.tags"
                    :key="t"
                    color="primary"
                    text-color="white"
                    @click="searchTerm = tag.title"
                  >{{ tag.title }}</v-chip>
                </v-card-text>
                <v-card-actions>
                  <v-btn
                    v-for="(action, a) in item.actions"
                    :key="a"
                    flat
                    dark
                    :class="item.colors ? item.colors.class : cardColors[i%cardColors.length].class"
                    :href="action.to"
                  >{{ action.text }}</v-btn>
                </v-card-actions>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      searchTerm: "",
      cardColors: [
        { color: "blue-grey darken-2", class: "white--text" },
        { color: "cyan lighten-2", class: "black--text" },
        { color: "deep-purple darken-2", class: "white--text" }
      ],
      items: [
        {
          description: `
            <div>
                <div class="headline">Personal Website</div>
                <span>
                Built as a way to organize my projects and have a public-facing profile, this is a single-page application
                built on Vue, Vuetify, and Nuxt. It is deployed as a static site.
                </span>
            </div>
          `,
          tags: [
            { title: "JavaScript" },
            { title: "ES6" },
            { title: "Vue" },
            { title: "Nuxt" },
            { title: "Material Design" },
            { title: "SPA" },
            { title: "Node.js" }
          ],
          actions: [
            {
              to: "/",
              text: "Project homepage"
            },
            {
              // make this the link to the GitHub for the project
              to: "https://github.com/philliard3/personal-site",
              text: "See the source code"
            }
          ]
        },
        {
          description: `
            <div>
                <div class="headline">Nurse Roster Builder</div>
                <span>
                An application to build out the requirements for a workforce of nurses, nurse practitioners, and doctors.
                Originally created as a part of UMBC's CMSC 447 course. In this project, I designed most of and implemented
                all of the UI side, which both compiled to an Electron app and transpiled to a web app. I also worked with
                the team member who implemented the algorithmic backend to make a JSON specification for mapping between
                the UI state and the input for the backend process.
                </span>
            </div>`,
          tags: [
            { title: "JavaScript" },
            { title: "ES6" },
            { title: "Vue" },
            { title: "Vuex" },
            { title: "Material Design" },
            { title: "SPA" },
            { title: "Electron" },
            { title: "Node.js" },
            { title: "JSON" },
            { title: "Java" },
            { title: "Optaplanner" }
          ],
          actions: [
            {
              to: "https://github.com/philliard3/CMSC447-application",
              text: "See this project"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filteredItems() {
      if (!this.searchTerm) {
        return this.items;
      }
      const items = [];

      this.items.forEach((item, itemIndex) => {
        const descriptionContains = item.description
          .toUpperCase()
          .includes(this.searchTerm.toUpperCase());
        if (descriptionContains) {
          items.push({
            colors: this.cardColors[itemIndex % this.cardColors.length],
            ...item
          });
          return;
        }
        const tagsContain = item.tags.some(tag =>
          tag.title.toUpperCase().includes(this.searchTerm.toUpperCase())
        );
        if (tagsContain) {
          items.push({
            colors: this.cardColors[itemIndex % this.cardColors.length],
            ...item
          });
          return;
        }
      });

      return items;
    }
  }
};
</script>

<style>
.no-underline {
  text-decoration: none;
  margin-left: 2%;
}
</style>
