<template>
  <v-container>
    <v-row justify="center" align="center" id="space">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title id="title">
            スマブラSPステージ選択アプリ
          </v-card-title>
          <v-card-text id="cardText">
            <div>これは名前の通り「大乱闘スマッシュブラザーズSP」のステージ選択アプリです。</div>
            <div>スマートフォンで使用することを想定していないのでWebサイトやタブレットから開くことをオススメします。</div>
            <div>ステージ画像の引用 : <a href="https://www.smashbros.com/ja_JP/stage/index.html" target="_brank">https://www.smashbros.com/ja_JP/stage/index.html</a></div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-btn
        outlined id="buttonSize" class="headline"
        nuxt to="/firstSelect"
      >
        start
      </v-btn>
    </v-row>
  </v-container>
</template>
<script>
  export default {
    components: {

    }
  }
</script>
<style scoped>
  @media screen and (min-width:0px) and ( max-width:600px){
    #space{
      padding-bottom: 10px;
    }

    #title{
      font-size: 16px;
    }

    #cardText{
      font-size: 10px;
    }

    #buttonSize{
      height: 70px;
      width: 140px;
    }
  }

  @media screen and (min-width:600px) and ( max-width:960px){
    #space{
      padding-bottom: 170px;
    }

    #title{
      font-size: 18px;
    }

    #cardText{
      font-size: 12px;
    }

    #buttonSize{
      height: 70px;
      width: 140px;
    }
  }

  @media screen and (min-width:960px) and ( max-width:1367px){
    #buttonSize{

    }
  }

  @media screen and (orientation: portrait) and (min-width:1023px) and ( max-width:1025px){
    #buttonSize{

    }

    #ipad_pro_size{
      /*
        ipad proの縦の長さと ipadの横の長さが同じなのに涙を流して書いた部分です
        なにか良い実装方法があれば教えていただけると幸いです
       */
    }
  }

  @media screen and (min-width:1367px) and ( max-width:2504px){
    #space{
      padding-bottom: 200px;
    }
    #buttonSize{
      height: 100px;
      width: 200px;
    }
  }

  @media screen and (min-width:2504px) and ( max-width:3000px){
    #buttonSize{

    }
  }


</style>
