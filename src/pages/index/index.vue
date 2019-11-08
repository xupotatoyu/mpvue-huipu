<template>
  <div class='container'>
     <div class="bar">
        <form>
            <input type="text" placeholder="  请输入您要搜索的内容...">
            <button type="submit"></button>
        </form>
    </div>
    <div class='header'>
      <div :class='{ active: tab==="all" }' @click.stop='changeTab($event)' data-tab='all' :data-offset='0'>关注</div>
      <div :class='{ active: tab==="good" }' @click.stop='changeTab($event)' data-tab='good' :data-offset='1'>推荐</div>
      <div :class='{ active: tab==="share" }' @click.stop='changeTab($event)' data-tab='share' :data-offset='2'>热榜</div>
      <div :class='{ active: tab==="job" }' @click.stop='changeTab($event)' data-tab='job' :data-offset='3'>最新</div>
    </div>
    <div class="containers" :animation='animation'>
      <div>
        <scroll-view scroll-y class='scroll-container' @scrolltolower='getMore'>
          <div>
            <card :item='item'></card>
          </div>
        </scroll-view>
      </div>
    </div>
  </div>
</template>

<script>
import card from "@/components/card";
import { getURL } from "../../utils/index";
export default {
  data() {
    return {
      page: 0,
      tab: "all",
      cardData: {
        all: [],
        good: [],
        share: [],
        job: [],
        ask: []
      },
      isLoading: false,
      list: ["all", "good", "share", "job", "ask"],
      animation: {}
    };
  },
  components: {
    card
  },
  watch: {},
  mounted() {
    this.getData("all", 0);
  }
}
</script>

<style lang="scss" scoped>
.container {
  background-color: rgb(245, 245, 249);
  font-size: 30rpx;
  overflow:hidden;
  width:100vw;
  .search-line {
    width: 100%;
    line-height: 86rpx;
    background-color: white;
  }
  /*搜索框*/
  .bar {
    background:white;
    width: 100%;
    line-height: 86rpx;
    }
  .bar input {
    width: 50%;
    border-radius: 42px;
    margin-left: 20rpx;
    border: 2px solid #324B4E;
  }
  .header {
    display: flex;
    width: 100%;
    background-color: white;
    & > div {
      width: 20%;
      color: black;
      text-align: center;
      height: 86rpx;
      line-height: 86rpx;
    }
  }
  .containers {
    display: flex;
    position: relative;
    .scroll-container {
      height: 90vh;
      width: 100vw;
    }
  }
}
.header .header > div + .header > div {
  border-left: 2rpx solid white;
}
.active {
  font-weight: bold;
}
</style>

