<template>
  <div>
    <p id="ipad_pro_size">{{DescriptionText[0].person}} : {{DescriptionText[0].text}}</p>
    <v-container>
      <v-row>
        <v-layout>
          <v-flex xs12>
            <v-btn @click="reject">Select</v-btn>
          </v-flex>
          <v-flex>
            <v-btn @click="reload">NextMatch</v-btn>
          </v-flex>
        </v-layout>
      </v-row>
    </v-container>
    <v-layout
      row
    >
      <v-flex
        xl4 lg6 md4 xs12
        v-for="(item, i) in items"
        :key="i"
      >
        <v-container>
          <v-row dense>
            <v-col>
              <v-card dark outlined>
                <v-card-title

                  v-text="item.stageName"
                >
                </v-card-title>
                <v-layout justify-center>
                  <v-avatar
                    class="ma-1"
                    size=""
                    tile
                    @click="item.select=!item.select"
                  >
                    <div v-if="item.select">
                      <v-img :src="item.picture" id="imageSize"></v-img>
                    </div>
                    <div v-else-if="item.firstReject && !item.secondReject">
                      <v-img :src="item.redPicture" id="imageSize"></v-img>
                    </div>
                    <div v-else-if="item.secondReject && !item.finalReject">
                      <v-img :src="item.bluePicture" id="imageSize"></v-img>
                    </div>
                    <div v-else-if="item.finalReject">
                      <v-img :src="item.checkPicture" id="imageSize"></v-img>
                    </div>
                  </v-avatar>
                </v-layout>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-flex>
    </v-layout>
  </div>
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
      },

      reload:function(){
        location.reload();
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
  @media screen and (min-width:0px) and ( max-width:600px){
    #imageSize{
      height:180px;
      width:320px;
    }
  }

  @media screen and (min-width:600px) and ( max-width:960px){
    #imageSize{
      height:270px;
      width:480px;
    }
  }

  @media screen and (min-width:960px) and ( max-width:1367px){
    #imageSize{
      height:162px;
      width:288px;
    }
  }

  @media screen and (orientation: portrait) and (min-width:1023px) and ( max-width:1025px){
    #imageSize{
      height:162px;
      width:288px;
    }

    #ipad_pro_size{
      padding-top:180px;
      /*
        ipad proの縦の長さと ipadの横の長さが同じなのに涙を流して書いた部分です
        なにか良い実装方法があれば教えていただけると幸いです
       */
    }
  }

  @media screen and (min-width:1367px) and ( max-width:2504px){
    #imageSize{
      height:270px;
      width:480px;
    }
  }

  @media screen and (min-width:2504px) and ( max-width:3000px){
    #imageSize{
      height:306px;
      width:544px;
    }
  }
</style>
