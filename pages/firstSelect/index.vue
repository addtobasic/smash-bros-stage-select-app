<template>
  <div>
    <p id="ipad_pro_size">{{DescriptionText.person}} : {{DescriptionText.text}}</p>
    <v-container>
      <v-row>
        <v-layout>
          <v-flex xs12>
            <v-btn @click="reject">Select</v-btn>
          </v-flex>
          <v-flex>
            <v-btn to="/secondAndSubsequentSelect">SecondMatch</v-btn>
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
                      <v-img :src="item.picture" :lazy-src="item.lazyImage" id="imageSize">
                        <template v-slot:placeholder>
                          <v-row
                            class="fill-height ma-0"
                            align="center"
                            justify="center"
                          >
                            <v-progress-circular
                              indeterminate
                              color="grey lighten-5"
                            ></v-progress-circular>
                          </v-row>
                        </template>
                      </v-img>
                    </div>
                    <div v-else-if="item.firstReject && !item.secondReject">
                      <v-img :src="item.redPicture" :lazy-src="item.lazyImage" id="imageSize">
                        <template v-slot:placeholder>
                          <v-row
                            class="fill-height ma-0"
                            align="center"
                            justify="center"
                          >
                            <v-progress-circular
                              indeterminate
                              color="grey lighten-5"
                            ></v-progress-circular>
                          </v-row>
                        </template>
                      </v-img>
                    </div>
                    <div v-else-if="item.secondReject && !item.finalReject">
                      <v-img :src="item.bluePicture" :lazy-src="item.lazyImage" id="imageSize">
                        <template v-slot:placeholder>
                          <v-row
                            class="fill-height ma-0"
                            align="center"
                            justify="center"
                          >
                            <v-progress-circular
                              indeterminate
                              color="grey lighten-5"
                            ></v-progress-circular>
                          </v-row>
                        </template>
                      </v-img>
                    </div>
                    <div v-else-if="item.finalReject">
                      <v-img :src="item.checkPicture" :lazy-src="item.lazyImage" id="imageSize">
                        <template v-slot:placeholder>
                          <v-row
                            class="fill-height ma-0"
                            align="center"
                            justify="center"
                          >
                            <v-progress-circular
                              indeterminate
                              color="grey lighten-5"
                            ></v-progress-circular>
                          </v-row>
                        </template>
                      </v-img>
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
          if(1 !== i )alert("じゃんけんの勝者は拒否ステージを1つ選択してください")
          else {
            rejectNum++
            this.items.forEach(function(item){
              if(item.select)item.secondReject = true
            })
            this.DescriptionText.person = "じゃんけん敗者"
            this.DescriptionText.text = "拒否ステージを2つ選択してください"
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
            this.DescriptionText.person = "じゃんけん勝者"
            this.DescriptionText.text = "残りのステージから対戦ステージを選択してください"
          }
        }
      }
    },

    data:()=>({
      DescriptionText:
      {
        person:"じゃんけん勝者",
        text:"拒否ステージを1つ選択してください"
      },

      items:[
        {
          stageName:"Final Destination",
          picture:require("static/stage/normal/finalDestination.png"),
          redPicture:require("static/stage/red/finalDestination_red.png"),
          bluePicture:require("static/stage/blue/finalDestination_blue.png"),
          checkPicture:require("static/stage/check/finalDestination_check.png"),
          lazyImage:"https://github.com/addtobasic/smash-bros-stage-select-app/blob/main/static/stage/normal/finalDestination.png?raw=true",
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
          lazyImage:"https://github.com/addtobasic/smash-bros-stage-select-app/blob/main/static/stage/normal/battleField.png?raw=true",
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
          lazyImage:"https://github.com/addtobasic/smash-bros-stage-select-app/blob/main/static/stage/normal/pokemonStadium2.png?raw=true",
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
          lazyImage:"https://github.com/addtobasic/smash-bros-stage-select-app/blob/main/static/stage/normal/townAndCity.png?raw=true",
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
          lazyImage:"https://github.com/addtobasic/smash-bros-stage-select-app/blob/main/static/stage/normal/smashVille.png?raw=true",
          select:true,
          firstReject:true,
          secondReject:false,
          finalReject:false,
        },
      ]
    })
  }
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
      padding-top:200px;
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
