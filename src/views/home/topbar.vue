<template>
  <link href="//at.alicdn.com/t/c/font_3755859_7s5y2zupr7.css" rel="stylesheet">
  <div class="topbar">
    <div class="left">
      <div class="music" @click="playClick();check()" :style="music">
        <i class="iconfont icon-musicfill"></i>
      </div>
    </div>
    <div class="right">
      <a href="https://fastjs.com.cn/" target="_blank">Fastjs</a>
      <a href="https://github.com/fastjs-team/" target="_blank">Team</a>
      <a href="https://github.com/dy-xiaodong2022/" target="_blank">Github</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "topbar",
  data() {
    return {
      music: {},
    }
  },
  mounted() {
    this.check()
  },
  methods: {
    check() {
      this.music = this.getAudio().paused ? {
        "color": "red",
        "border-color": "red",
        "animation-play-state": "paused"
      } : {}
    },
  },
  props: {
    playClick: {
      type: Function,
      default: () => {}
    },
    getAudio: {
      type: Function,
      default: () => {}
    }
  }
}
</script>

<style lang="less" scoped>
.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;

  .music {
    height: 26px;
    width: 26px;
    border: 1px solid #b2b2b2;
    color: #b2b2b2;
    border-radius: 100%;
    display: inline-block;
    position: relative;
    cursor: pointer;
    animation: spin 5s linear infinite;

    > i {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  a {
    height: 100%;
    padding: 0 6px;
    margin: 0 10px;
    color: #b0b0b0;
    transition: 0.4s color;
    display: inline-block;
    line-height: 40px;
    font-size: 16px;

    &:hover {
      color: #ececec;
    }
  }
}
</style>