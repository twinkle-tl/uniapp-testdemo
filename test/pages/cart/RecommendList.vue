<template>
    <view class="container">
        <view class="top-img">
            <image src="../../static/images/guessulike.jpg" mode=""></image>
        </view>
        <view class="list">
            <view class="item" v-for="(item,index) of [1,2,3,4,5,6]" :key="index">
                <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/7906b53fe38d4d6427f210e7f18425d0.jpg?thumb=1&w=360&h=360" mode=""></image>
                <text class="desc ellipsis">Redmi K20 Pro 6GB+64GB</text>
                <view class="price">
                    <text>￥2499</text>
                    <text class="old-price">￥3499</text>
                </view>
            </view>
        </view>
    </view>
</template>

<script>
export default{
    name:'RecommendList'
}
</script>

<style scoped>
    .container {
      background: #fff;
      padding-bottom: 90rpx;
    }
    .container .top-img {
      height: 125rpx;
      margin-bottom: 4rpx;
    }
    .container .top-img image {
      width: 100%;
      height: 100%;
    }
    .container .list {
      display: flex;
      flex-wrap: wrap;
    }
    .container .list .item {
      display: flex;
      flex-direction: column;
      width: 50%;
      height: 489.2rpx;
      box-sizing: border-box;
      margin-bottom: 22rpx;
    }
    .container .list .item:nth-child(odd) {
      padding-right: 2rpx;
    }
    .container .list .item:nth-child(even) {
      padding-left: 2rpx;
    }
    .container .list .item image {
      width: 100%;
      height: 100%;
      padding-bottom: 16rpx;
    }
    .container .list .item .desc {
      padding: 0 26rpx 20rpx;
    }
    .container .list .item .price {
      padding-left: 20rpx;
    }
    .container .list .item .price text:nth-child(1) {
      color: #ff6700;
      font-size: 30rpx;
    }
    .container .list .item .price .old-price {
      font-size: 22rpx;
      padding-left: 8rpx;
      color: rgba(0,0,0,0.541);
      text-decoration: line-through;
    }
</style>
