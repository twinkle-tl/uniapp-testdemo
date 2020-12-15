<template>
	<view class="container">
        <!-- <view class="status_bar"></view> -->
		<view class="login-logo flex-col">
            <image src="../../static/images/mi_logo.jpg" mode=""></image>
            <text>小米账号登录</text>
        </view>
        <view class="input-container">
            <view class="input-wrapper mobile">
                <input type="text" value="" placeholder-class="placeholder-class" placeholder="手机号码"/>
            </view>
            <view class="input-wrapper code flex-row">
                <input type="text" value="" placeholder-class="placeholder-class" placeholder="短信验证码" />
                <text>获取验证码</text>
            </view>
        </view>
        <view class="btn bg flex-center">立即登录/注册</view>
        <view class="btn flex-center">用户名密码登录</view>
        <view style="padding-top: 38rpx;color: #9b9b9b;text-align: center;">收不到验证码?</view>
        <view class="other">
            <view class="title"><text>其它方式登录</text></view>
            <view class="list flex-center">
                <image src="../../static/images/wechat.png" mode=""></image>
            </view>
        </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
    .container {
      padding: 0 40rpx;
    }
    .container .login-logo {
      padding-top: 60rpx;
      padding-bottom: 16rpx;
    }
    .container .login-logo image {
      width: 96rpx;
      height: 96rpx;
      padding-bottom: 30rpx;
    }
    .container .login-logo text {
      color: #000;
      font-size: 36rpx;
    }
    .container .input-container {
      font-size: 34rpx;
    }
    .container .input-container .placeholder-class {
      font-size: 36rpx;
      color: #9b9b9b;
    }
    .container .input-container .input-wrapper {
      height: 108rpx;
      border-bottom: 2rpx solid #d3d3d3;
    }
    .container .input-container .input-wrapper input {
      width: 100%;
      height: 100%;
    }
    .container .input-container .mobile {
      padding-left: 128rpx;
      position: relative;
    }
    .container .input-container .mobile:before {
      content: "+86";
      position: absolute;
      left: 10rpx;
      top: 50%;
      transform: translateY(-50%);
      color: #9b9b9b;
    }
    .container .input-container .code input {
      flex: 1;
    }
    .container .input-container .code text {
      width: 140rpx;
      padding: 0 40rpx;
      color: #2ea5e5;
      font-size: 28rpx;
    }
    .container .btn {
      height: 88rpx;
      margin-top: 48rpx;
      font-size: 36rpx;
      cursor: pointer;
      border-radius: 12rpx;
      overflow: hidden;
      border: 2rpx solid #d3d3d3;
    }
    .container .btn.bg {
      color: #fff;
      background-color: #ff6700;
      border: 0;
    }
    .container .other {
      padding-top: 80rpx;
    }
    .container .other .title {
      padding-bottom: 30rpx;
      text-align: center;
      color: #b0b0b0;
    }
    .container .other .title text {
      position: relative;
    }
    .container .other .title text:before,
    .container .other .title text:after {
      content: "";
      position: absolute;
      top: 50%;
      width: 100%;
      border-top: 2rpx solid #f2f2f2;
    }
    .container .other .title text:before {
      left: 0;
      transform: translate(-110%, -50%);
    }
    .container .other .title text:after {
      right: 0;
      transform: translate(110%, -50%);
    }
    .container .other .list image {
      width: 90rpx;
      height: 90rpx;
      border-radius: 50%;
    }

</style>
