<template>
  <div class="container">
    <div class='list'>
      <span>标题:</span>
      <input class='input' type="text" placeholder="最少10个字" v-model="title">
    </div>
    <picker class='picker' @change="bindPickerChange($event)" :value="index" :range="pickerData">
      <span>选择主题:</span><span style='margin-left:400rpx;'>{{pickerData[index]}}</span>
    </picker>
    <textarea style="border:0;border-radius:5px;background-color:rgba(241,241,241,.98);width: 355px;height: 100px;padding: 10px;resize: none;" placeholder="请输入"></textarea>
    <div class="bottom-button" @click.stop="handle">
        <div>
            发布
        </div>
    </div>
    <div class="addimg"></div>
    <div class="addimg"></div>
    <div class="addimg"></div>
  </div>
</template>

<script>s
import wemark from "mpvue-wemark";
export default {
  components: {
    login,
    wemark
  },

  watch: {
    content(next) {
      console.log(next);
    }
  },
  data() {
    return {
      pickerData: [],
      index: "3",
      title: "",
      content: "",
      visible: false,
      tab: "markdown" // or preview
    };
  }
};
</script>

<style lang='scss' scoped>
.container {
  height: 100vh;
  background-color: white;
  .list {
    display: flex;
    justify-content: space-between;
    background-color: white;
    line-height: 70rpx;
    padding: 0 30rpx;
    .input {
      height: 90rpx;
      line-height: 90rpx;
    }
  }
  .picker {
    display: flex;
    justify-content: space-between;
    background-color: white;
    line-height: 70rpx;
    padding: 0 30rpx;
  }
  .tabs {
    display: flex;
    background-color: white;
    & > div {
      width: 50%;
      text-align: center;
    }
  }
  .textarea {
    width: 100%;
    background-color: white;
    margin-bottom: 30rpx;
    height: 500rpx;
    padding: 0 30rpx;
    box-sizing: border-box;
  }
}
.selected {
  color: $color;
  border-bottom: 2rpx solid $color;
}
.bottom-button {
    position: absolute;
    bottom: 0px;
    width: 100%;
    height:97rpx;
    background-color: white;
    display: flex;
    align-items: center;
}
.bottom-button > div {
    width:80%;
    line-height:80rpx;
    color: white;
    font-size:36rpx;
    background:rgba(251,63,17,1);
    border-radius:10px;
    border:2px solid rgba(5,5,5,0.08);
    margin: 0 auto;
    text-align: center;
}
.addimg {
 background: url("../../../static/adding.png") no-repeat center center;
 margin-left: 20rpx;
 margin-top: 10rpx;
 background-size: cover;
 display: inline-block;
 width: 150rpx;
 height: 150rpx;
}
</style>
