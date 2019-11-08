<template>
  <div class='container'>
     <div class='body'>
       <div class='tabs'>
         <div class='unread'>未读消息:23</div>
         <div class='read' >已读消息</div>
       </div>
        <div>
        <div class='notice'>
          <div class="title">
            <span>大灰狼</span>在<span style='color:rgb(65, 184, 131);'>tcp/ip</span>中回复了你
          </div>
          <div class='content'>
            您好请问一下，是不是是是是是是所所所所所所所
          </div>
          <div class="number">
            2019年11月4日
          </div>
        </div>
        <div class='notice'>
          <div class="title">
            <span>大灰狼</span>在<span style='color:rgb(65, 184, 131);'>tcp/ip</span>中回复了你
          </div>
          <div class='content'>
            您好请问一下，是不是是是是是是所所所所所所所
          </div>
          <div class="number">
            2019年11月4日
          </div>
        </div>
       </div>
     </div>
  </div>
</template>
<script>
import { passTime } from "../../utils/index";
export default {
}
</script>

<style lang='scss' scoped>
.container {
  background-color: rgb(245, 245, 249);
  width: 100vw;
  .body {
    display: flex;
    flex-direction: column;
    .tabs {
      display: flex;
      background-color: white;
      & > div {
        width: 50%;
        text-align: center;
      }
    }
    .notice {
      background-color: white;
      margin-bottom: 5rpx;
      padding: 30rpx;
      .title {
        font-size: 30rpx;
      }
      .content {
        padding-left: 10rpx;
        margin: 10rpx 0;
        overflow: hidden;
        font-size: 27rpx;
        text-overflow: ellipsis;
      }
      .number {
      color: $borderColor;
      font-size: 26rpx;
      & + & {
        margin-left: 20rpx;
      }
    }
    }
    .read-all {
      color: $color;
      border: 2rpx solid $color;
      font-size: 20rpx;
      width: 99rpx;
      border-radius: 20rpx;
      height: 46rpx;
      line-height: 46rpx;
      text-align: center;
      padding: 0;
      margin: 10rpx;
    }
  }
}
.selected {
  color: $color;
  border-bottom: 2rpx solid $color;
}
</style>

