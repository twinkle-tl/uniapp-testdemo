<template>
    <view>
        <navigator url="../login/login">
            <view class="default-row more-right">
                <text>登录后享受更多优惠</text>
                <text>去登录</text>
            </view>
        </navigator>
        <view class="noitems">
            <text>购物车还是空的</text>
            <text>去逛逛</text>
        </view>
    </view>
</template>

<script>
export default{
    name:'NoLogin'
}
</script>

<style scoped>
    .default-row {
      height: 108rpx;
      padding-left: 33rpx;
      font-size: 34rpx;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .default-row text:nth-child(1) {
      font-size: 34rpx;
    }
    .default-row text:nth-child(2) {
      font-size: 26rpx;
      color: rgba(0,0,0,0.541);
    }
    .noitems {
      height: 80rpx;
      padding: 21rpx 0;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #ebebeb;
    }
    .noitems text:nth-child(1) {
      display: inline-block;
      line-height: 80rpx;
      background: url("https://m.mi.com/static/img/cartnull.daaf7926f8.png") no-repeat 0;
      background-size: auto 100%;
      padding: 0 16rpx 0 96rpx;
      color: rgba(0,0,0,0.27);
    }
    .noitems text:nth-child(2) {
      border: 2rpx solid rgba(0,0,0,0.15);
      padding: 0 24rpx;
    }

</style>
