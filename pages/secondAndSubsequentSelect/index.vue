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
                <v-img :src="item.picture" id="size"></v-img>
              </div>
              <div v-else-if="item.firstReject && !item.secondReject">
                <v-img :src="item.redPicture" id="size"></v-img>
              </div>
              <div v-else-if="item.finalReject">
                <v-img :src="item.checkPicture" id="size"></v-img>
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
            <v-avatar
              class="ma-3"
              size="450"
              tile
              @click="item.select=!item.select"
            >
              <div v-if="item.select">
                <v-img :src="item.picture" id="size"></v-img>
              </div>
              <div v-else-if="item.firstReject && !item.secondReject">
                <v-img :src="item.redPicture" id="size"></v-img>
              </div>
              <div v-else-if="item.finalReject">
                <v-img :src="item.checkPicture" id="size"></v-img>
              </div>
            </v-avatar>
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
          if(item.select === false){
            i++;
          }
        })

        if(rejectNum === 0){
          if(2 !== i )alert("前回の試合の勝者は拒否ステージを2つ選択してください")
          else {
            rejectNum++
            this.items.forEach(function(item){
              if(item.select){
                item.secondReject = true
                item.finalReject = true
              }
            })
            this.DescriptionText[0].person = "前回の試合の敗者"
            this.DescriptionText[0].text = "対戦するステージを選択してください"
          }
        }
      }
    },
    data:()=>({
      DescriptionText:[
        {
          person:"前回の試合の勝者",
          text:"拒否ステージを2つ選択してください"
        }
      ],

      items:[
        {
          stageName:"Final Destination",
          picture:require("static/stage/normal/finalDestination.png"),
          redPicture:require("static/stage/red/finalDestination_red.png"),
          checkPicture:require("static/stage/check/finalDestination_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
        {
          stageName:"Battle Field",
          picture:require("static/stage/normal/battleField.png"),
          redPicture:require("static/stage/red/battleField_red.png"),
          checkPicture:require("static/stage/check/battleField_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
        {
          stageName:"Pokemon Stadium2",
          picture:require("static/stage/normal/pokemonStadium2.png"),
          redPicture:require("static/stage/red/pokemonStadium2_red.png"),
          checkPicture:require("static/stage/check/pokemonStadium2_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
        {
          stageName:"Town and City",
          picture:require("static/stage/normal/townAndCity.png"),
          redPicture:require("static/stage/red/townAndCity_red.png"),
          checkPicture:require("static/stage/check/townAndCity_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
        {
          stageName:"Smash Ville",
          picture:require("static/stage/normal/smashVille.png"),
          redPicture:require("static/stage/red/smashVille_red.png"),
          checkPicture:require("static/stage/check/smashVille_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
        {
          stageName:"Kalos Pokemon League",
          picture:require("static/stage/normal/kalosPokemonLeague.png"),
          redPicture:require("static/stage/red/kalosPokemonLeague_red.png"),
          checkPicture:require("static/stage/check/kalosPokemonLeague_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
        {
          stageName:"Lylat",
          picture:require("static/stage/normal/lylat.png"),
          redPicture:require("static/stage/red/lylat_red.png"),
          checkPicture:require("static/stage/check/lylat_check.png"),
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
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
