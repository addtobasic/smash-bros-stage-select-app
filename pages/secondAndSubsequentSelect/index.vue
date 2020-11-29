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


        // else if(rejectNum === 1){
        //   if(3 !== i )alert("じゃんけん敗者側は拒否ステージを2つ選択してください")
        //   else {
        //     rejectNum++
        //     console.log(rejectNum)

        //     this.DescriptionText[0].person = "じゃんけん勝者側"
        //     this.DescriptionText[0].text = "残りのステージから最後の拒否ステージを選んでください"
        //   }
        // }


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
          picture:require("static/stage/finalDestination.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/finalDestination_selected.jpeg")
        },
        {
          stageName:"Battle Field",
          picture:require("static/stage/battleField.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/battleField_selected.jpeg")
        },
        {
          stageName:"Pokemon Stadium2",
          picture:require("static/stage/pokemonStadium2.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/pokemonStadium2_selected.jpeg")
        },
        {
          stageName:"Town and City",
          picture:require("static/stage/townAndCity.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/townAndCity_selected.jpeg")
        },
        {
          stageName:"Smash Ville",
          picture:require("static/stage/smashVille.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/smashVille_selected.jpeg")
        },
        {
          stageName:"Kalos Pokemon League",
          picture:require("static/stage/kalosPokemonLeague.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/kalosPokemonLeague_selected.jpeg")
        },
        {
          stageName:"Lylat",
          picture:require("static/stage/lylat.jpeg"),
          select:false,
          selectedPicture:require("static/selected_stage/lylat_selected.jpeg")
        },
      ]
    }
    )}
</script>
<style>
  #size{
    height:250px;
  }
</style>
