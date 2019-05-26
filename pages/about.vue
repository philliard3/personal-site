<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md8>
      <v-container>
        <v-card>
          <v-card-title class="display-2 font-weight-light">About Me</v-card-title>
          <v-card-text>
            <p>I am an incoming PhD student at the University of Pennsylvania.</p>
            <p>
              I have held internship positions at Goldman Sachs and Johns Hopkins
              University Applied Physics Laboratory.
            </p>
            <p>
              I have held student research positions at Oregon State University
              and the University of Maryland, Baltimore County.
            </p>
            <p>
              My current interests are in linked data and increasing the accessibility
              of average individuals to the graph of data relevant to their lives.
            </p>
          </v-card-text>
          <v-card-actions>
            <v-spacer/>
            <v-btn color="primary" outline dark nuxt to="/projects">See my work</v-btn>
          </v-card-actions>
        </v-card>
      </v-container>
    </v-flex>
  </v-layout>
</template>
