<template>
  <div class="title">
    <div class="image-avatar"></div>
    <div class="break-line"></div>
    <span class="nickname">dy-xiaodong2022</span>
    <span class="sign">没有什么一帆风顺，路上的艰辛只有自己知道</span>
  </div>
</template>

<script>
export default {
  name: "Title"
}
</script>

<style lang="less" scoped>
.title {
  margin-left: 10vw;
  margin-top: 40vh;
  position: relative;

  .image-avatar {
    width: 100px;
    height: 100px;
    background: url(avatar.jpg) no-repeat;
    background-size: cover;
    border-radius: 100%;
  }

  .break-line {
    width: 0;
    height: 1px;
    background: #b2b2b2;
    margin-top: 20px;
    position: absolute;
    top: 70px;
    left: 50px;
    // animation
    animation: break-line 3s forwards;
    z-index: -1;
  }

  // animation
  @keyframes break-line {
    0% {
      width: 0;
    }
    100% {
      width: 500px;
    }
  }

  span {
    position: absolute;
  }

  .nickname {
    top: 40px;
    left: 120px;
  }

  .sign {
    top: 60px;
    left: 120px;
  }
}

// screen < 800px
@media screen and (max-width: 800px) {
  .title {
    .break-line {
      display: none;
    }
  }
}
</style>