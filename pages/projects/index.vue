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
              <v-card :color="item.colors.color" :class="item.colors.class">
                <v-card-title primary-title v-html="item.description" />
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
                    :class="item.colors.class"
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
            { title: "ES2015" },
            { title: "Vue" },
            { title: "Nuxt" },
            { title: "Material Design" },
            { title: "SPA" },
            { title: "Node.js" }
          ],
          actions: [
            {
              to: "https://www.seas.upenn.edu/~pdh/",
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
        },
        {
          description: `
            <div>
              <div class="headline">Natural Language Processing Research</div>
              <span>
                With funding from an Undergraduate Research Award from UMBC, I conducted experiments to inform
                machine learning models for sentiment detection. With Dr. Frank Ferraro's advisory, I designed
                the associated experiments, created a small web application to act as a survey for the experiment,
                and trained natural language processing models based on that data. I presented my progress at UMBC's
                Undergraduate Research and Creative Achievement Day during a poster session.
                <div>
                  <strong>2018-2019</strong>
                </div>
              </span>
            </div>
          `,
          tags: [
            { title: "Research" },
            { title: "Machine Learning" },
            { title: "Natural Language Processing" },
            { title: "Python" },
            { title: "JavaScript" },
            { title: "UMBC" },
            { title: "Undergrad" }
          ]
        },
        {
          colors: {
            color: "#7399C6",
            class: "white--text"
          },
          description: `
            <div>
              <div class="headline">Goldman Sachs Internships</div>
              <span>
                <div>
                  During my summers in 2018 and 2019, I was at Goldman Sachs as a Summer Analyst.
                  While there, I had the opportunity to work with various technologies having to do with
                  messaging frameworks and interfacing with usage data from those messaging operations.
                  <ul>
                    <li>
                      My summer 2018 project involved collecting graph-based data about messaging service usage.
                      I built a full-stack service which injested this data into a JanusGrah instance and
                      served it as JSON to a graph representation as a component in a larger React application.
                    </li>
                    <li>
                      My summer 2019 project involved collecting messaging usage data from a variety of sources
                      and building a dashboard of analysis metrics. The data collection and processing was done
                      using the Apache Kafka Java API. The analysis dashboard was built in Kibana after being
                      inserted into an Elasticsearch database.
                    </li>
                  </ul>
                  <strong>Summer 2018, Summer 2019</strong>
                </div>
              </span>
            </div>
          `,
          tags: [
            { title: "React" },
            { title: "JavaScript" },
            { title: "Java" },
            { title: "Graphs" },
            { title: "JanusGraph" },
            { title: "Gremlin" },
            { title: "Tinkerpop" },
            { title: "Kafka" },
            { title: "Elasticsearch" }
          ]
        },
        {
          description: `
            <div>
              <div class="headline">Comic Tracking Extension</div>
              <span>
                <div>
                  This is web scraping and RSS subscription application that builds and tracks a database of
                  webcomics and their updates. The backend service is to be accompanied by a Google Chrome
                  Extension that stores a local list of comics and checks in with the backend for updates.
                  This project is part of an ongoing effort of mine to create a suite of tools that allow
                  users to keep track of and support artists whose work they love.
                </div>
                <div>
                  <strong>Ongoing</strong>
                </div>
              </span>
            </div>
          `,
          tags: [
            { title: "TypeScript" },
            { title: "JavaScript" },
            { title: "Node.js" },
            { title: "Chrome Extension" }
          ],
          actions: [
            {
              /** Add the project link when it becomes public **/
              to: "#",
              text: "Coming Soon"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filteredItems() {
      if (!this.searchTerm) {
        return this.items.map((item, itemIndex) => ({
          colors:
            item.colors || this.cardColors[itemIndex % this.cardColors.length],
          ...item
        }));
      }
      const itemsToShow = [];

      this.items.forEach((item, itemIndex) => {
        const descriptionContains = item.description
          .toUpperCase()
          .includes(this.searchTerm.toUpperCase());
        if (descriptionContains) {
          itemsToShow.push({
            colors:
              item.colors ||
              this.cardColors[itemIndex % this.cardColors.length],
            ...item
          });
          return;
        }
        const tagsContain = item.tags.some(tag =>
          tag.title.toUpperCase().includes(this.searchTerm.toUpperCase())
        );
        if (tagsContain) {
          itemsToShow.push({
            colors:
              item.colors ||
              this.cardColors[itemIndex % this.cardColors.length],
            ...item
          });
          return;
        }
      });

      return itemsToShow;
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
