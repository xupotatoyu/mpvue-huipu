<template>
  <div class='container' @click.stop="goDetail($event)">
    <div class='head'>
      <img class='head-img' src='../../static/touxiang.jpg' :data-loginname='item.author.loginname' @click.stop='goAuthorPage'>
      <div class='info'>
        <span>回旋加速喷气式阿姆斯特朗炮</span>
        <span class='time'>20:58</span>
      </div>
      <span class="top">置顶</span>
    </div>
    <div>
      <p>当客户端和服务器通过三次握手建立了TCP连接以后，当数据传送完毕，肯定是要断开TCP连接的啊。那对于TCP的断开连接，这里就有了神秘的“四次挥手”</p>
    </div>
    <div class='foot'>
      <div class='count'>
        <span class='number'>浏览：123</span>
      </div>
      <div class='later'>
        <span class='number'>点赞：22</span>
      </div>
    </div>
  </div>
</template>

<script>
import { passTime } from "../utils/index";
export default {

}
</script>

<style lang='scss'  scoped>
.container {
  height: 330rpx;
  padding: 30rpx;
  margin-bottom: 20rpx;
  background-color: white;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  .head {
    color: $color;
    display: flex;
    align-items: center;
    .head-img {
      width: 64rpx;
      height: 64rpx;
    }
    .info {
      flex-direction: column;
      display: flex;
      margin-left: 26rpx;
      .time {
        color: $borderColor;
      }
    }
    .top {
      position: absolute;
      right: 40rpx;
      color: red;
    }
  }
  .body {
    color: $color;
    & > p {
      font-weight: bold;
    }
  }
  .foot {
    display: flex;
    justify-content: space-between;
    .number {
      color: $borderColor;
      font-size: 26rpx;
      & + & {
        margin-left: 20rpx;
      }
    }
  }
}
</style>
