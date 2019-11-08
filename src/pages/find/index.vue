<template>
  <div class='container'>
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
export default {
   components: {
    card
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
</style>

