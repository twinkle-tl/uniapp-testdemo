<template>
    <scroll-view class="list-container" 
        :scroll-y="true" 
        :scroll-into-view="'item'+currentNav" 
        :show-scrollbar="false"
        :scroll-with-animation="true">
        <view class="list" v-for="(item,index) of list" :key="index" :id="'item'+index">
            <view class="top-img"><image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/83408c0d8871bfabd20b0b12f7362568.jpg?thumb=1&w=500&h=200" mode=""></image></view>
            <view class="title"><text>手机{{index}}</text></view>
            <view class="item-container">
                <view class="item" v-for="(item,index) of [1,2,3,4,5]" :key="index">
                    <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/efd0aa03675839c8f20e8c38de8229c1.png?thumb=1&w=120&h=120" mode=""></image>
                    <view class="name">Redmi K30 4G</view>
                </view>
            </view>
        </view>
    </scroll-view>
</template>

<script>
export default {
    name:'ContentList',
    props:{
        currentNav:{
            type: String
        }
    },
    data() {
        return {
            list: Array(16).fill(1)
        }
    },
}
</script>
<style scoped>
    .list-container {
      padding-right: 32rpx;
      position: absolute;
      z-index: 999;
      overflow: hidden;
      top: 0;
      left: 192rpx;
      right: 0;
      bottom: 0;
      width: calc(100% - 192rpx);
      box-sizing: border-box;
    }
    .list-container .top-img {
      height: 208rpx;
    }
    .list-container .top-img image {
      width: 100%;
      height: 100%;
    }
    .list-container .title {
      height: 132rpx;
      line-height: 132rpx;
      text-align: center;
    }
    .list-container .title >text {
      position: relative;
    }
    .list-container .title >text:before,
    .list-container .title >text:after {
      content: "";
      position: absolute;
      top: 50%;
      width: 40rpx;
      border-top: 2rpx solid #e0e0e0;
    }
    .list-container .title >text:before {
      left: 0;
      transform: translate(-150%, -50%);
    }
    .list-container .title >text:after {
      right: 0;
      transform: translate(150%, -50%);
    }
    .list-container .item-container {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
    }
    .list-container .item-container .item {
      width: 33.33%;
      text-align: center;
      padding-top: 21rpx;
      padding-bottom: 31rpx;
    }
    .list-container .item-container .item image {
      width: 104rpx;
      height: 104rpx;
      margin-bottom: 28rpx;
    }
    .list-container .item-container .item .name {
      font-size: 23rpx;
      color: rgba(0,0,0,0.541);
    }
</style>
