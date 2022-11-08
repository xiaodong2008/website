<template>
  <div class="home">
    <topbar :playClick="playClick" :getAudio="getAudio"/>
    <Title/>
    <Bottom />
  </div>
  <div class="snow-wrapper"></div>
</template>

<script>
import {FastjsDom, selecter as $} from "fastjs-next";
import Title from "@/views/home/title";
import Topbar from "@/views/home/topbar";
import {message} from "ant-design-vue";
import Bottom from "@/views/home/bottom";

export default {
  name: "index",
  components: {
    Bottom,
    Title,
    Topbar
  },
  setup() {
    // bg music
    const mp3 = require("./bg_1.mp3");
    const audio = new Audio(mp3);
    audio.loop = true;
    // set volume
    audio.volume = 0.4;
    audio.play();
    // check is play
    if (audio.paused) message.warn("背景音乐播放被拦截，您可以手动点击播放");

    return {
      audio
    }
  },
  mounted() {
    // snow
    const addSnow = () => {
      // rand
      const rand = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
      const el = new FastjsDom("div").attr("class", "snow").appendTo($(".snow-wrapper").getEl().el());
      let height = 0;
      let addHeight = rand(10, 25);
      el.css({
        left: rand(0, 100) + "%",
      })
      const timer = setInterval(() => {
        height += addHeight;
        el.css("top", height + "px");
        // if out of document
        if (el.el().getBoundingClientRect().top > document.documentElement.clientHeight) {
          clearInterval(timer);
          el.remove();
        }
      }, 100);
      setTimeout(addSnow, rand(100, 600));
    };
    addSnow()
  },
  methods: {
    playClick() {
      this.audio.paused ? this.audio.play() : this.audio.pause();
    },
    getAudio() {
      return this.audio;
    }
  }
}
</script>

<style lang="less">
a:link {
  text-decoration: none;
}

html {
  background: #131111;
  overflow-x: hidden;
  padding: 10px;

  body {
    background: transparent;
  }
}

#app {
  span {
    color: #dadada;
    font-size: 15px;
    font-weight: 300;
    font-family: initial;
  }
}

// snow
.snow-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: -1;
  pointer-events: none;
  overflow: hidden;
}

.snow {
  position: absolute;
  left: 0;
  top: 0;
  width: 4px;
  height: 4px;
  border-radius: 100%;
  background: #fff;
  transition: 1s;;
}
</style>