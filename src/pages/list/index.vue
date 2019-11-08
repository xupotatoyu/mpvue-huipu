<template>
  <div class="container">
    <div class='margin' v-for='item in currentData' :key='item.id'>
      <card :item='item' :hidden='true'></card>
    </div>
  </div>
</template>

<script>
import card from "../../components/card";
export default {
  data() {
    return {
      currentData: []
    };
  },
  components: {
    card
  }
}
</script>
<style lang='scss' scoped>
.container {
  background-color: rgb(245, 245, 249);
  min-height: 100vh;
  .margin {
    margin-bottom: 20rpx;
  }
}
</style>
