# audio-player-vue

> A audio player plugin with vue2.

## public
``` bash
npm run build

npm publish --access public

```
## Build Setup

``` bash
npm i audio-player-vue

import AudioPlayer from 'audio-player-vue'
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

### Usage
```
<AudioPlayer
  simple
  :src="require('./assets/audio.ogg')"
>
<AudioPlayer
  backplay
  :src="require('./assets/audio.ogg')"
>
<AudioPlayer
  :src="require('./assets/audio.ogg')"
>
```

### Options
+ src - video的路径
+ autopay: Boolean
+ controls: Boolean
+ muted
+ loop
+ simple - 只保留一个播放/暂定按钮
+ backplay - 针对打开时直接播放的audio，只保留一个静音/有声按钮
ps: simple 和backplay不可以同时存在