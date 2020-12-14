<template>
  <v-app dark>
    <v-app-bar
      app
    >
      <a href="/" style="color:white;">
        <v-toolbar-title v-text="title" />
      </a>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      app
      dark
    >
      <div>つくったひと <a href="https://twitter.com/genshi0916" target="_blank">げんし</a></div>
      <div class="flex-grow-1"></div>
      <div><v-icon>mdi-gmail</v-icon>genshi0916@gmail.com</div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      title: 'Smash Bros. stage select app'
    }
  }
}
</script>
<style>
  a {
    text-decoration: none;
  }
</style>
