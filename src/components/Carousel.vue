<!--

filename: Carousel.vue
description: Component for showing random images of campus as a banner on the Dashboard

author: Gabe Landau <gll1872@rit.edu>

-->

<template>
  <div class="carousel">
    <div id="carousel" :style="{ 'background-image': 'url(' + backgroundImage + ')' }">
				<div class="slogan">
					<h1>We've got your back</h1>
					<div>
						<p>Visualize and track the projects that we're working on to improve your path through RIT.</p>
					</div>
				</div>
			</div>
  </div>
</template>

<script>
import Images from '../mixins/images'

export default {
  name: 'carousel',
  mixins: [Images],
  data () {
    return {
      backgroundImage: this.getRandomImage()
    }
  },
  methods: {
    getRandomImage () {
      let images = this.getImages()
      let random = Math.floor(Math.random() * images.length)
      return images[random]
    }
  }
}
</script>

<style scoped>
#carousel {
	text-align: center;
	color: white;
	height: 400px;
  background: no-repeat fixed;
  -webkit-background-size: cover;
	-moz-background-size: cover;
	-o-background-size: cover;
	background-size: cover;
}

#carousel h1 {
	cursor: default;
	padding: 0;
	margin: 0;
	text-transform: uppercase;
}

.slogan {
	display: inline-block;
	width: 100%;
	max-width: 400px;
	position: relative;
	top: 50%;
	transform: translateY(-50%);
}
</style>
