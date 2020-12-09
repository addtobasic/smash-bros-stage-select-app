<template>
  <v-app dark>
    <h1 v-if="error.statusCode === 404">
      {{ pageNotFound }}
    </h1>
    <h1 v-else>
      {{ otherError }}
    </h1>
      <NuxtLink to="/">
      Home page
    </NuxtLink>
    <div class="animation" id="icon">
      <img class="img1" src="../static/img/genshi_line_animated.svg" alt="genshi_svg">
      <img class="img2" src="../static/img/icon.jpg" alt="icon_img">
    </div>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
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
h1 {
  font-size: 20px;
}


#icon {
  height: 40vh;
  width: 40vh;
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
