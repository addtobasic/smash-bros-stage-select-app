<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title class="headline">
            スマブラSPステージ選択アプリ
          </v-card-title>
          <v-card-text class="subtitle-1">
            <div>これは名前の通り「大乱闘スマッシュブラザーズSP」のステージ選択アプリです。</div>
            <div>ステージ画像の引用 : <a href="https://www.smashbros.com/ja_JP/stage/index.html" target="_brank">https://www.smashbros.com/ja_JP/stage/index.html</a></div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row justify="center" align="center">
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
    // Logo,
  }
}
</script>
<style>


  #buttonSize{
    height: 100px;
    width: 200px;
  }
</style>
