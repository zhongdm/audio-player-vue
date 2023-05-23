<template>
  <div>
    <div class="inline" v-if="simple"
      @click="onPlayAudio">
      <span
        class="simple-audio play-size"
        :style="{backgroundImage: 'url('+require('../assets/icon/'+ playIcon) + ')'}"
        ></span>
    </div>
    <div class="inline" v-if="!simple && backPlay" @click="onToggleAudio">
    <span
      class="simple-audio"
      :style="{backgroundImage: 'url('+require('../assets/icon/'+ volumeIcon) + ')'}"
      ></span>
    </div>
    <audio
      ref="audio"
      v-show="!simple && !backPlay"
      :autoplay="autoplay"
      :controls="isControls"
      :loop="loop"
      :muted="muted"
      :src="src"
      @ended="onEnded"
      >
    </audio>
  </div>
</template>

<script>
  export default {
    name: 'audio-player-vue',
    props: {
      autoplay: {
        type: Boolean,
        default: false
      },
      controls: {
        type: Boolean,
        default: true
      },
      buffered: {

        type: Boolean,
        default: true
      },
      loop: {
        type: Boolean,
        default: false
      },
      muted: {
        type: Boolean,
        default: true
      },
      preload: {

        type: Boolean,
        default: true
      },
      src: String,
      volume: {

        type: Boolean,
        default: true
      },
      simple: {
        type: Boolean,
        default: false
      },
      backPlay: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        volumeIcon: 'volume_close.svg',
        playIcon: 'play.svg'
      }
    },
    watch: {
      muted(val, oldVal) {
        if (val) {
          this.$refs.audio.volume  = 0
        }
      }
    },
    computed: {
      isAutoPlay() {
        return this.autoplay ? 'autoplay' : null
      },
      isControls() {
        return this.controls ? 'controls' : null
      },
    },
    methods: {
      onPlayAudio() {
        const audio = this.$refs.audio
        this.playIcon = audio.paused ? 'pause.svg' : 'play.svg' 
        if (audio.paused) {
          audio.play()
        } else {
          audio.pause()
        }
      },
      onToggleAudio() {
        const audio = this.$refs.audio
        this.volumeIcon = audio.volume === 0 ? 'volume.svg' : 'volume_close.svg'
        audio.volume = audio.volume === 0 ? 1 : 0
      },
      onEnded(args) {
        this.volumeIcon = args.target.ended ? 'volume_close.svg' : 'volume.svg'
        this.playIcon = args.target.ended ? 'play.svg' : 'pause.svg'
      }
    }
  }
</script>

<style scoped>
.inline {
  display: inline-block;
  width: 25px;
  height: 25px;
  border: 1px solid #000;
  border-radius: 50%;
}
.simple-audio {
  display: inline-block;
  width: 100%;
  height: 100%;
  padding: 5px;
  border-radius: 50%;
  background-size: contain;
  box-sizing: border-box;
}
.play-size {
  transform: scale(0.7);
}
</style>
