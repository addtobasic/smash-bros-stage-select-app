<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <p>rock-paper-scissors winner</p>
      <p>Please select one rejection stage.</p>
      <v-col
        v-for="(item, i) in items"
        :key="i"
        cols="12"
      >

        <v-card dark>
          <div class="justify-space-between" v-if="$vuetify.breakpoint.mobile">
            <div>
              <v-card-title
                class="headline"
                v-text="item.stageName"
              ></v-card-title>
            </div>
            <a v-bind:href="item.url" target="_blank">
              <v-avatar
                class="ma-3"
                size="230"
                tile
              >
                <v-img :src="item.picture" id="size"></v-img>
              </v-avatar>
            </a>
          </div>

          <div class="d-flex justify-space-between" v-if="!$vuetify.breakpoint.mobile">
            <div>
              <v-card-title
                class="headline"
                v-text="item.stageName"
              ></v-card-title>
            </div>
            <a v-bind:href="item.url" :target="item.target">
              <v-avatar
                class="ma-3"
                size="450"
                tile
              >
                <v-img :src="item.picture" id="size"></v-img>
              </v-avatar>
            </a>
          </div>
        </v-card>
      </v-col>
    </v-flex>
  </v-layout>
</template>
<script>
  export default{
    name:'about',
    components:{

    },
    data () {
      return {
        items:[
          {
            stageName:"finalDestination",
            picture:require("static/stage/finalDestination.jpeg"),
          },
          {
            stageName:"battleField",
            picture:require("static/stage/battleField.jpeg"),
          },
          {
            stageName:"pokemonStadium2",
            picture:require("static/stage/pokemonStadium2.jpeg"),
          },
          {
            stageName:"townAndCity",
            picture:require("static/stage/townAndCity.jpeg"),
          },
          {
            stageName:"smashVille",
            picture:require("static/stage/smashVille.jpeg"),
          },
          {
            stageName:"kalosPokemonLeague",
            picture:require("static/stage/kalosPokemonLeague.jpeg"),
          },
          {
            stageName:"lylat",
            picture:require("static/stage/lylat.jpeg"),
          },
        ]
      }
    }
  }
</script>
<style>
  #size{
    height:250px;
  }
</style>
