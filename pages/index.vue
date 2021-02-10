<template>
  <div class="container">
    <div :style="moveWithMouse" class="cursor" />
    <div class="video-wrapper">
      <h2 class="title">
        {{ title }}
      </h2>
      <h2 class="title title-sec">
        {{ title }}
      </h2>
      <video class="video" autoplay loop muted playsinline>
        <source src="/demo-video.mp4" type="video/mp4">
      </video>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data: () => ({
    title: 'Hello World',
    x: 0,
    y: 0
  }),
  computed: {
    moveWithMouse () {
      return {
        left: `${this.x}px`,
        top: `${this.y}px`
      }
    }
  },
  mounted () {
    if (document) {
      document.addEventListener('mousemove', (e) => {
        this.x = e.pageX
        this.y = e.pageY
      })
    }
  }
})
</script>

<style>
.video-wrapper {
  position: relative;
}

.cursor {
  position: fixed;
  width: 70px;
  height: 70px;
  background: #000;
  border-radius: 50%;
  z-index: 99;
}

.container {
  cursor: none;
}

.video {
  width: 100%;
}

.title {
  position: absolute;
  font-weight: bold;
  color: #fff;
  text-transform: uppercase;
  font-size: 3.8rem;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.title-sec {
  -webkit-text-fill-color: transparent; /* Will override color (regardless of order) */
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #fff;
  z-index: 999;
}
</style>
