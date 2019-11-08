<template>
  <div  class='container'>
      <sendReply v-if='sendVisible' @close-modal='closeModal' @reply-success='replySuccess' :content='content' :topicId='id' :replyId='replyId'></sendReply>
    <div>
      <div class='header'>
        <div class='author'>
          <img class='author-img' :src='detailData.author && detailData.author.avatar_url' alt="头像">
          <span class='name'>{{detailData.author&& detailData.author.loginname}}</span>
        </div>
        <div class='list'><img @click.stop="collect" :src="detailData.is_collect?'/static/star2.png':'/static/star1.png'" style='width:40rpx;height:40rpx;'><span>楼主</span></div>
      </div>
      <scroll-view class='body' scroll-y='true'   @scroll='onScroll($event)' :scroll-top="top" enable-back-to-top='true' @scrolltolower='getMore'>
        <div class='title'>
          <p class='big'>{{detailData.title}}</p>
          <div class='time-info'>
            <span>发布于:{{formatCreateAt}}</span>
            <span>浏览:{{detailData.visit_count}}</span>
            <span>评论:{{detailData.reply_count}}</span>
          </div>
        </div>
        <img class='up-png' src="/static/up.png" mode='widthFix' @click.stop="goTop">
        <div v-if='!sendVisible' class='reply-buton' @click.stop="showReplyModal">评论</div>
        <div class='content'>
          <wemark :mdData='detailData.content'></wemark>
        </div>
        <div class='reply'>
          <div>评论：</div>
          <div class='reply-container' v-for='(item,originindex) in formatReplies' :key='item.id' :data-id='item.id'>
            <div class='head'>
              <img class='head-img' :src='item.author.avatar_url' :data-loginname='item.author.loginname' @click.stop='goAuthorPage'>
              <div class='info'>
                <span>{{item.author.loginname}}</span>
                <span class='time'>{{item.create_at}}</span>
              </div>
            </div>
            <p class='reply-content'>
              <wemark :mdData='item.content'></wemark>
            </p>
            <div class='foot'>
              <div :data-replyid='item.id' :data-originindex='originindex' @click.stop="upOrCancel($event)"><img class='icon' :src="(!item.is_uped)?'/static/good1.png':'/static/good2.png'" /><span>点赞:{{item.ups.length}}</span></div>
              <div :data-loginname='item.author.loginname' @click.stop="showReplyModal($event)" :data-replyid='item.id'><img class='icon' src='/static/chat.png' /><span>回复</span></div>
            </div>
          </div>
        </div>
      </scroll-view>
    </div>
  </div>
</template>

<script>
import { passTime, debounce} from "../../utils";
import sendReply from "../../components/sendReply";
import wemark from "mpvue-wemark";
const debounceOnScroll = () => debounce(function(e){
  this.top = e.target.scrollTop
});
export default {
  components: {
    wemark,
    sendReply
  }
};
</script>

<style lang='scss' scoped>
.container {
  height: 100vh;
  background-color: rgb(245, 245, 239);
  .header {
    display: flex;
    justify-content: space-between;
    background-color: white;
    margin-bottom: 20rpx;
    padding: 30rpx;
    .author {
      color: $color;
      display: flex;
      align-items: center;
      .author-img {
        width: 64rpx;
        height: 64rpx;
      }
      .name {
        margin-left: 20rpx;
      }
    }
    .list {
      display: flex;
      align-items: center;
    }
  }
  .body {
    height: 90vh;
  }
  .title {
    background-color: white;
    margin-bottom: 20rpx;
    padding: 30rpx;
    .big {
      font-size: 50rpx;
    }
    .time-info {
      display: flex;
      justify-content: space-around;
    }
  }
  .reply-buton {
    border-radius: 50%;
    width: 100rpx;
    height: 100rpx;
    text-align: center;
    font-size: 30rpx;
    position: fixed;
    line-height: 100rpx;
    background-color: $color;
    top: 86vh;
    left: 81vw;
    color: white;
  }
  .up-png {
    width: 100rpx;
    top: 75vh;
    left: 81vw;
    position: fixed;
  }
  .content {
    background-color: white;
    margin-bottom: 20rpx;
    padding: 30rpx;
  }
}
.reply {
  background-color: white;
  margin-bottom: 20rpx;
  padding: 30rpx;
  .reply-container {
    padding: 30rpx;
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
    }
    .reply-content {
      font-size: 40rpx;
      & + & {
        border-top: 2rpx solid $borderColor;
      }
    }
    .foot {
      display: flex;
      & > div {
        margin-right: 20rpx;
        display: flex;
        align-items: center;
      }
      .icon {
        width: 56rpx;
        height: 56rpx;
      }
    }
  }
}
</style>
