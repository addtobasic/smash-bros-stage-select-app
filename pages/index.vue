<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="12" xs="12" sm="10" md="10" lg="10" xl="8">
        <v-card>
          <v-card-title id="title">
            スマブラSPステージ選択アプリ
          </v-card-title>
          <v-card-text id="cardText">
            <li>これは名前の通り「大乱闘スマッシュブラザーズSP」のステージ選択アプリです。</li>
            <li>スマートフォンで使用することを想定していないのでPCやタブレットから開くことをオススメします。</li>
            <li>ソースコードは<a href="https://github.com/Genshi0916/smash-bros-stage-select-app" target="_brank">こちら</a></li>
            <li>ステージ画像の引用 : <a href="https://www.smashbros.com/ja_JP/stage/index.html" target="_brank">https://www.smashbros.com/ja_JP/stage/index.html</a></li>
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
    #title{
      font-size: 15px;
    }

    #cardText{
      font-size: 9px;
    }

    #buttonSize{
      height: 70px;
      width: 140px;
    }
  }

  @media screen and (min-width:600px) and ( max-width:960px){
    #title{
      font-size: 18px;
    }

    #cardText{
      font-size: 12px;
    }

    #buttonSize{
      height: 100px;
      width: 200px;
    }
  }

  @media screen and (min-width:960px) and ( max-width:1367px){
    #title{
      font-size: 20px;
    }

    #cardText{
      font-size: 14px;
    }

    #buttonSize{
      height: 150px;
      width: 300px;
    }
  }

  @media screen and (min-width:1367px) and ( max-width:2504px){
    #title{
      font-size: 22px;
    }

    #cardText{
      font-size: 16px;
    }

    #buttonSize{
      height: 170px;
      width: 340px;
    }
  }

  @media screen and (min-width:2504px) and ( max-width:3000px){
    #title{
      font-size: 24px;
    }

    #cardText{
      font-size: 18px;
    }

    #buttonSize{
      height: 170px;
      width: 340px;
    }
  }
</style>
