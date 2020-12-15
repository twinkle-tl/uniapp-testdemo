<template>
	<view class="main-container">
        <!-- 布局一 -->
		<view class="panel" v-for="(item,index) of [1,2]" :key="index">
            <view class="title-img">
                <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/e32eea5c3c27062019f9ac6434b351df.jpg?thumb=1&w=720&h=440" mode=""></image>
            </view>
            <view class="list">
                <view class="item" v-for="(item,index) of [1,2,3,4]" :key="index">
                    <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/53e729d30746033a042d8ae9399553a7.jpg?thumb=1&w=344&h=280" mode=""></image>
                    <view class="name">Redmi Note 8 Pro</view>
                    <view class="desc">6400万全场景四摄</view>
                    <view class="price">
                        <text>￥1299</text>
                        <text>￥1399</text>
                    </view>
                    <view class="btn">立即购买</view>
                </view>
            </view>
            <view class="more">更多小米产品 ></view>
        </view>
        <!-- 布局二 -->
        <view class="layout-2">
            <view class="title-img"><image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/df9f0ec1b502e3f7ca36779c7596c7c4.jpg?thumb=1&w=720&h=440" mode=""></image></view>
            <view class="list">
                <view class="item" 
                    :class="{reverse:index&1}" 
                    v-for="(item,index) of [1,2,3,4]" 
                    :key="index">
                    <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/c33f008a86c151a1500d44d599351256.jpg?thumb=1&w=360&h=360" mode=""></image>
                    <view class="right">
                        <view class="name">小爱音箱万能遥控板</view>
                        <view class="desc">传统家电秒变智能</view>
                        <view class="price">
                            <text>￥149</text>
                            <text>￥199</text>
                        </view>
                    </view>
                </view>
            </view>
            <view class="more">更多小米产品 ></view>
        </view>
        <!-- 布局三 -->
        <view class="layout-3">
            <view class="list">
                <view class="item" v-for="(item,index) of [1,2,3,4,5,6]" :key="index">
                    <image src="https://i8.mifile.cn/v1/a1/46c44f3e-479d-a999-dd2d-98fb39b51e17.webp" mode=""></image>
                </view>
            </view>
        </view>
        <view class="know">
            <image src="https://cdn.cnbj0.fds.api.mi-img.com/b2c-mimall-media/bbb5bac8089d890338b5bf8ff742cbbc.png?thumb=1&w=720&h=106" mode=""></image>
        </view>
        <!-- <view class="fixed-br">
            <image class="money" src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/a5bd951d960c0ad6ea2c54770edfb2ff.gif" mode=""></image>
            <image class="go-top" src="https://m.mi.com/static/img/top.451d650ecd.png" mode=""></image>
        </view> -->
	</view>
</template>

<script>
	export default {
        name:'HomeMain',
		data() {
			return {
				
			}
		},
		methods: {
			
		},
        
	}
</script>

<style scoped>
    .main-container .panel {
      background: #fff;
      margin-bottom: 16rpx;
    }
    .main-container .panel .title-img {
      height: 458rpx;
      margin-bottom: 7rpx;
    }
    .main-container .panel .title-img image {
      width: 100%;
      height: 100%;
    }
    .main-container .panel .list {
      padding: 0 12.5rpx;
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
    .main-container .panel .list .item {
      width: calc(50% - 6.25rpx);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-bottom: 21rpx;
    }
    .main-container .panel .list .item image {
      width: 100%;
      height: 291.6rpx;
      margin-bottom: 21rpx;
    }
    .main-container .panel .list .item .name {
      font-size: 26rpx;
      color: rgba(0,0,0,0.871);
      padding-bottom: 6rpx;
    }
    .main-container .panel .list .item .desc {
      padding-bottom: 6rpx;
      font-size: 22rpx;
      color: rgba(0,0,0,0.541);
    }
    .main-container .panel .list .item .price {
      padding-bottom: 4rpx;
    }
    .main-container .panel .list .item .price text:nth-child(1) {
      font-size: 28rpx;
      color: #ea625b;
      padding-right: 10rpx;
    }
    .main-container .panel .list .item .price text:nth-child(1):after {
      content: "起";
      font-size: 22rpx;
      color: #ea625b;
    }
    .main-container .panel .list .item .price text:nth-child(2) {
      font-size: 22rpx;
      color: rgba(0,0,0,0.541);
      text-decoration: line-through;
    }
    .main-container .panel .list .item .btn {
      width: 200rpx;
      background: #ea625b;
      border-radius: 5rpx;
      text-align: center;
      color: #fff;
      font-size: 24rpx;
      padding: 16rpx 0;
      font-weight: 700;
    }
    .main-container .panel .more {
      height: 104rpx;
      line-height: 104rpx;
      text-align: center;
      color: rgba(0,0,0,0.6);
      font-size: 30rpx;
    }
    .main-container .layout-2 {
      background: #fff;
      margin-bottom: 16rpx;
    }
    .main-container .layout-2 .title-img {
      height: 458rpx;
      margin-bottom: 7rpx;
    }
    .main-container .layout-2 .title-img image {
      width: 100%;
      height: 100%;
    }
    .main-container .layout-2 .list .item {
      height: 375rpx;
      display: flex;
    }
    .main-container .layout-2 .list .item.reverse {
      flex-direction: row-reverse;
    }
    .main-container .layout-2 .list .item >image {
      width: 50%;
      height: 100%;
    }
    .main-container .layout-2 .list .item .right {
      width: 50%;
      box-sizing: border-box;
      padding: 64rpx 12rpx 0 32rpx;
    }
    .main-container .layout-2 .list .item .right .name {
      font-size: 30rpx;
      color: rgba(0,0,0,0.871);
      padding-bottom: 6rpx;
    }
    .main-container .layout-2 .list .item .right .desc {
      padding-bottom: 26rpx;
      font-size: 22rpx;
      color: rgba(0,0,0,0.541);
    }
    .main-container .layout-2 .list .item .right .price text:nth-child(1) {
      font-size: 28rpx;
      color: #ea625b;
      padding-right: 10rpx;
    }
    .main-container .layout-2 .list .item .right .price text:nth-child(2) {
      font-size: 22rpx;
      color: rgba(0,0,0,0.541);
      text-decoration: line-through;
    }
    .main-container .layout-2 .more {
      height: 104rpx;
      line-height: 104rpx;
      text-align: center;
      color: rgba(0,0,0,0.6);
      font-size: 30rpx;
    }
    .main-container .layout-3 {
      background: #fff;
      margin-bottom: 16rpx;
    }
    .main-container .layout-3 .list {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
    }
    .main-container .layout-3 .list .item {
      height: 500rpx;
      width: calc(50% - 2rpx);
    }
    .main-container .layout-3 .list .item:nth-last-child(n+2) {
      margin-bottom: 4rpx;
    }
    .main-container .layout-3 .list .item image {
      width: 100%;
      height: 100%;
    }
    .main-container .know {
      height: 112rpx;
    }
    .main-container .know image {
      width: 100%;
      height: 100%;
    }
    .main-container .fixed-br {
      position: fixed;
      bottom: calc(var(--window-bottom) + 40rpx);
      right: 26rpx;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .main-container .fixed-br .money {
      width: 116rpx;
      height: 116rpx;
      margin-bottom: 16rpx;
    }
    .main-container .fixed-br .go-top {
      width: 73rpx;
      height: 73rpx;
    }
</style>    
