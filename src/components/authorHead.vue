<template>
  <div class='header'>
    <img src='../../static/touxiang.jpg' class='img'>
    <span class='span'>回旋加速喷气式阿姆斯特朗炮</span>
    <span class='span'>关注：100</span>
    <span class='span'>粉丝：200</span>
  </div>
</template>
<script>
import { passTime } from "../utils/index";
export default {
  props: {
    user: Object
  },
  computed: {
    formatCreateAt() {
      return passTime(this.user && this.user.create_at).slice(0, -1);
    }
  }
};
</script>

<style lang='scss' scoped>
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: $color;
  font-size: 30rpx;
  background-color: white;
  .img {
    width: 200rpx;
    height: 200rpx;
    border-radius: 50%;
    margin-top: 30rpx;
  }
  .span {
    margin-top: 20rpx;
  }
}
</style>
