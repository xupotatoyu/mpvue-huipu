<template>
  <div class="container">
    <authorHead></authorHead>
    <div class='list'>
      <div class="jiantou">
        <span>我的收藏</span>
        <a></a>
      </div>
      <div class="jiantou">
        <span>最近发布</span>
        <a></a>
      </div>
      <div class="jiantou">
        <span>最近回复</span>
        <a></a>
      </div>
      <div class="jiantou">
        <span>退出</span>
        <a></a>
      </div>
    </div>
  </div>
</template>

<script>
import { getURL } from "../../utils/index";
import authorHead from "../../components/authorHead";
export default {
  data() {
    return {
      visible: false,
      user:{}
    };
  },
  components: {
    authorHead,
    login
  }
}
</script>

<style lang='scss' scoped>
.container {
  height: 100vh;
  background-color: rgb(245, 245, 249);
  .jiantou {
    position: relative;
    line-height: 70rpx;
    width: 100%;
    background-color: white;
    margin-bottom: 5rpx;
  }
  .jiantou span {
      display: inline-block;
      margin-left: 25rpx;
      width:83%;
      white-space: pre-wrap;
      font-size:30rpx;
      font-family:PingFangSC;
      font-weight:400;
      color:rgba(0,0,0,1);
      line-height:70rpx;
  }
  .jiantou a {
      display: inline-block;
      position: absolute;
      top: 20rpx;
      height: 30rpx;
      line-height: 70rpx;
      width: 17%;
      background: url("../../../static/jiantou.png") no-repeat center center;
  }
}
</style>
