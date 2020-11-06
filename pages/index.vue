<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <div class="text-center">
        <!-- <logo /> -->
        <!-- <vuetify-logo /> -->
      </div>
      <v-card>
        <v-card-actions>
          <v-btn
            color="primary"
            nuxt
            to="/firstSelect"
          >
            start
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
// import Logo from '~/components/Logo.vue'


export default {
  components: {
    // Logo,
  }
}
</script>
