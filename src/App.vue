<template>
  <div id="app">
    <AudioPlayerVue
      simple
      :src="require('./assets/audio.ogg')"
    ></AudioPlayerVue>
    <AudioPlayerVue
      backPlay
      :autoplay="true"
      :muted="true"
      :src="require('./assets/audio.ogg')"
    ></AudioPlayerVue>
    <AudioPlayerVue
      :src="require('./assets/audio.ogg')"
    ></AudioPlayerVue>
  </div>
</template>

<script>
import AudioPlayerVue from './components/AudioPlayerVue.vue';

export default {
  name: 'video-player-vue-app',
  components: {
    AudioPlayerVue
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted() {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.audio-pp {
  width: 25px;
  height: 25px;
  /* margin: 10px;
  padding: 5px;
  border: 1px solid #000;
  border-radius: 50%; */
}
</style>
