<template>
  <div>
    <p>{{DescriptionText[0].person}}</p>
    <p>{{DescriptionText[0].text}}</p>
    <v-btn @click="reject">Next</v-btn>
    <v-layout
      row
    >
      <v-flex
        xl4 lg6
        v-for="(item, i) in items"
        :key="i"
      >
        <v-container>
          <v-row dense>
            <v-col>
              <v-card dark>
                <div class="justify-space-between" v-if="!$vuetify.breakpoint.mobile">
                  <v-card-title
                    class="headline"
                    v-text="item.stageName"
                  >
                  </v-card-title>
                  <v-layout justify-center>
                    <v-avatar
                      class="ma-3"
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
                </div>
                <div class="d-flex justify-space-between" v-if="$vuetify.breakpoint.mobile">
                  <div>
                    <v-card-title
                      class="headline"
                      v-text="item.stageName"
                    ></v-card-title>
                  </div>
                  <v-layout justify-center>
                  <v-avatar
                      class="ma-3"
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

                </div>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-flex>
    </v-layout>
    <v-btn to="/secondAndSubsequentSelect">SecondMatch</v-btn>
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
            console.log("画像のfalseの数"+i)
          }
        })

        if(rejectNum === 0){
          if(1 !== i )alert("じゃんけんの勝者は拒否ステージを1つ選択してください")
          else {
            rejectNum++
            this.items.forEach(function(item){
              if(item.select)item.secondReject = true
            })
            this.DescriptionText[0].person = "じゃんけん敗者"
            this.DescriptionText[0].text = "拒否ステージを2つ選択してください"
          }
        }

        else if(rejectNum === 1){
          if(3 !== i )alert("じゃんけんの敗者は拒否ステージを2つ選択してください")
          else {
            rejectNum++
            this.items.forEach(function(item){
              if(item.select)
              item.finalReject = true
            })
            this.DescriptionText[0].person = "じゃんけん勝者"
            this.DescriptionText[0].text = "残りのステージから対戦ステージを選択してください"
          }
        }
      }
    },

    data:()=>({
      DescriptionText:[
        {
          person:"じゃんけん勝者",
          text:"拒否ステージを1つ選択してください"
        }
      ],

      items:[
        {
          stageName:"Final Destination",
          picture:require("static/stage/normal/finalDestination.png"),
          redPicture:require("static/stage/red/finalDestination_red.png"),
          bluePicture:require("static/stage/blue/finalDestination_blue.png"),
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
          bluePicture:require("static/stage/blue/battleField_blue.png"),
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
          bluePicture:require("static/stage/blue/pokemonStadium2_blue.png"),
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
          bluePicture:require("static/stage/blue/townAndCity_blue.png"),
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
          bluePicture:require("static/stage/blue/smashVille_blue.png"),
          checkPicture:require("static/stage/check/smashVille_check.png"),
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
      height:90px;
      width:160px;
    top: 200px;

    }
  }

  @media screen and (min-width:600px) and ( max-width:960px){
    #imageSize{
      height:270px;
      width:480px;
    top: 200px;

    }
  }

  @media screen and (min-width:960px) and ( max-width:1264px){
    #imageSize{
      height:270px;
      width:480px;
    top: 200px;

    }
  }

    @media screen and (min-width:1264px) and ( max-width:2504px){
    #imageSize{
      height:270px;
      width:480px;
      /* top: 200px; */
    }
  }
</style>

//メディアクエリを当てるところから
