<template>
  <v-app dark>
    <v-card
      class="mx-auto"
      max-width="700"
      outlined
    >
      <v-list-item three-line>
        <v-list-item-content>
          <div class="overline mb-4" v-if="error.statusCode === 404">
              {{ pageNotFound }}
          </div>
          <div v-else>
            {{ otherError }}
          </div>
          <v-list-item-title class="headline mb-1">
            <NuxtLink to="/">Go back to the top page.</NuxtLink>
          </v-list-item-title>
        </v-list-item-content>

        <div class="animation" id="icon">
          <img class="img1" src="../static/img/genshi_line_animated.svg" alt="genshi_svg">
          <img class="img2" src="../static/img/icon.jpg" alt="icon_img">
        </div>
      </v-list-item>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          outlined
          rounded
          text
          @click="loadingFunction"
        >
          <v-icon>mdi-reload</v-icon>
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>

function loadingFunction() {
  var url = "./static/genshi_line_animated.svg?r=" + Math.random();
  document.querySelector("#icon img").setAttribute("src", url);
  loaderScreen = setTimeout(showPage, 4000);
}

export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },

  methods: {
    loadingFunction:function(){
      var url = "./static/genshi_line_animated.svg?r=" + Math.random();
      document.querySelector("#icon img").setAttribute("src", url);
      loaderScreen = setTimeout(showPage, 4000);
    }
  },

  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred',
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>

<style scoped>

#icon {
  width: 300px;
  background-color: white;
}

.animation {
	margin: auto;
	position: relative;
}

.animation img {
	width: 50%;
}

.animation .img1 {
	display: block;
	margin: 0 auto;
}

.animation .img2 {
	position: absolute;
	top: 0;
	left: 25%;
}

@keyframes animation {
	0% {
		opacity: 0;
	}

	12.5% {
		opacity: 0;
	}

	25.5% {
		opacity: 0;
	}
	37.5% {
		opacity: 0;
  }
  50% {
		opacity: 1;
  }
}
  .animation img {
    animation-name: animation;
    animation-duration: 7s;
    animation-iteration-count: 1;
  }

  .animation .img1 {
    animation-delay:5s;
  }

</style>
