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
      <p>{{DescriptionText[0].person}}</p>
      <p>{{DescriptionText[0].text}}</p>
      <v-btn @click="reject">Next</v-btn>

      <v-col
        v-for="(item, i) in items"
        :key="i"
        cols="12"
      >

        <v-card dark>
          <div class="justify-space-between" v-if="!$vuetify.breakpoint.mobile">
            <div>
              <v-card-title
                class="headline"
                v-text="item.stageName"
              ></v-card-title>
            </div>
              <v-avatar
                class="ma-3"
                size="450"
                tile
                @click="item.select=!item.select"
              >
                <div v-if="item.select">
                  <v-img :src="item.selectedPicture" id="size"></v-img>
                </div>
                <div v-else>
                  <v-img :src="item.picture" id="size"></v-img>
                </div>
              </v-avatar>
          </div>

          <div class="d-flex justify-space-between" v-if="$vuetify.breakpoint.mobile">
            <div>
              <v-card-title
                class="headline"
                v-text="item.stageName"
              ></v-card-title>
            </div>
            <!-- <a v-bind:href="item.url" :target="item.target"> -->
              <v-avatar
                class="ma-3"
                size="450"
                tile
                @click="item.select=!item.select"
              >
                <div v-if="item.select">
                  <v-img :src="item.selectedPicture" id="size"></v-img>
                </div>
                <div v-else>
                  <v-img :src="item.picture" id="size"></v-img>
                </div>
              </v-avatar>
            <!-- </a> -->
          </div>
        </v-card>
      </v-col>
        <v-btn ><a href="/secondAndSubsequentSelect" style="color:white;">Next Match</a></v-btn>
    </v-flex>
  </v-layout>
</template>
<script>
  let rejectNum = 0;

  export default{
    name:'about',
    components:{

    },

    methods:{
      reject:function(){
        let i=0;

        this.items.forEach(function(item){
          if(item.select === true){
            i++;
          }
        })

        if(rejectNum === 0){
          if(2 !== i )alert("前回の試合の勝者は拒否ステージを2つ選んでください")
          else {
            rejectNum++
            console.log(rejectNum)

            this.DescriptionText[0].person = "前回の試合の敗者"
            this.DescriptionText[0].text = "対戦ステージを選んでください"
          }
        }
      }
    },
  data:()=>({
      DescriptionText:[
        {
          person:"前回の試合の勝者",
          text:"拒否ステージを2つ選んでください"
        }
      ],

      items:[
        {
          stageName:"Final Destination",
          picture:require("static/stage/normal/finalDestination.png"),
          redPicture:require("static/stage/red/finalDestination_red.png"),
          bluePicture:require("static/stage/blue/finalDestination_blue.png"),
          checkPicture:require("static/stage/check/finalDestination_check.png"),
          select:false,
        },
        {
          stageName:"Battle Field",
          picture:require("static/stage/normal/battleField.png"),
          redPicture:require("static/stage/red/battleField_red.png"),
          bluePicture:require("static/stage/blue/battleField_blue.png"),
          checkPicture:require("static/stage/check/battleField_check.png"),
          select:false,
        },
        {
          stageName:"Pokemon Stadium2",
          picture:require("static/stage/normal/pokemonStadium2.png"),
          redPicture:require("static/stage/red/pokemonStadium2_red.png"),
          bluePicture:require("static/stage/blue/pokemonStadium2_blue.png"),
          checkPicture:require("static/stage/check/pokemonStadium2_check.png"),
          select:false,
        },
        {
          stageName:"Town and City",
          picture:require("static/stage/normal/townAndCity.png"),
          redPicture:require("static/stage/red/townAndCity_red.png"),
          bluePicture:require("static/stage/blue/townAndCity_blue.png"),
          checkPicture:require("static/stage/check/townAndCity_check.png"),
          select:false,
        },
        {
          stageName:"Smash Ville",
          picture:require("static/stage/normal/smashVille.png"),
          redPicture:require("static/stage/red/smashVille_red.png"),
          bluePicture:require("static/stage/blue/smashVille_blue.png"),
          checkPicture:require("static/stage/check/smashVille_check.png"),
          select:false,
        },



        {
          stageName:"Kalos Pokemon League",
          picture:require("static/stage/normal/kalosPokemonLeague.png"),
          redPicture:require("static/stage/red/kalosPokemonLeague_red.png"),
          bluePicture:require("static/stage/blue/kalosPokemonLeague_blue.png"),
          checkPicture:require("static/stage/check/kalosPokemonLeague_check.png"),
          select:false,
        },
        {
          stageName:"Lylat",
          picture:require("static/stage/normal/lylat.png"),
          redPicture:require("static/stage/red/lylat_red.png"),
          bluePicture:require("static/stage/blue/lylat_blue.png"),
          checkPicture:require("static/stage/check/lylat_check.png"),
          select:false,
        },
      ]
    }
    )}
</script>
<style>
  #size{
    height:270px;
    width:480px;
  }
</style>
