<template>
  <v-layout column justify-center align-center>
    <v-flex xs6 sm8 md8>
      <v-container>
        <v-layout row wrap>
          <v-flex xs12>
            <v-card id="main-info" outline>
              <v-card-title
                class="display-2 green--text text--darken-1"
                primary-title
              >Phillip Hilliard</v-card-title>
              <v-img :src="profilePicture" aspect-ratio="1.1" />
              <v-card-text>
                <div>
                  <ul>
                    <li>Research</li>
                    <li>Service</li>
                    <li>Fun</li>
                  </ul>
                </div>
              </v-card-text>
              <v-card-actions>
                <v-btn to="/about" flat outline>About me</v-btn>
                <v-btn to="/projects" flat outline>Projects</v-btn>
                <v-btn to="/social" flat outline>Contact</v-btn>
              </v-card-actions>
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
      profilePicture:
        "https://media.licdn.com/dms/image/C4D03AQGqi0HYSVHVBQ/profile-displayphoto-shrink_200_200/0?e=1573689600&v=beta&t=B2JiSMeKVL46l8iLoy4BTQzGuwrHy_dowIbAEBtL__Q"
    };
  }
};
</script>
