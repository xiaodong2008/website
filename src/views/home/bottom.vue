<template>
  <div class="bottom">
    <span>商务合作: xiaodong@indouyin.cn</span>
    <a-divider type="vertical" />
    <span>© 2022 dy-xiaodong2022</span>
  </div>
</template>

<script>
export default {
  name: "bottom"
}
</script>

<style lang="less" scoped>
.bottom {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  justify-content: center;

  .ant-divider-vertical {
    border-color: #b2b2b2;
  }
}
</style>