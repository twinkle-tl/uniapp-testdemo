<template>
	<view class="container">
		<view class="header-bar flex-row">
            <navigator class="icon-back" open-type="navigateBack"></navigator>
            <input type="text" placeholder="搜索商品名称" />
            <!-- #ifdef H5 || APP-PLUS -->
            <navigator class="icon-search" url="./detail"></navigator>
            <!-- #endif -->
        </view>
        <view class="main-container">
            <view class="hot-container">
                <view class="title">热门搜索</view>
                <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/595792fad7d29470726f0765091c323c.jpg?w=1080&h=300&bg=FFFFFF" mode=""></image>
                <view class="list">
                    <view class="item" v-for="(item,index) of [1,2,3,4]" :key="index">小米手环4</view>
                </view>
            </view>
            <view class="common-container">
                <view class="title">常用分类</view>
                <view class="list">
                    <view class="item" v-for="(item,index) of [1,2,3,4,5,6,7,8,9,0]" :key="index">手机</view>
                </view>
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
      padding-top: calc(var(--status-bar-height) + 82rpx);
    }
    .container .header-bar {
      position: fixed;
      z-index: 99;
      top: var(--status-bar-height);
      width: 100%;
      padding-right: 200rpx;
      box-sizing: border-box;
      height: 66rpx;
    }
    .container .header-bar .icon-back {
      width: 52rpx;
      height: 52rpx;
      background: no-repeat center url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAYAAABV7bNHAAABfUlEQVR4AWL4//8/oH1zzA4gCMJgbNv239i2beP+R8gXczpmV79XB9ja3UEDDJCAIAQhCEF/TBAgCEEIUkSKFrEoahD0VFCdOLtmWxQh6E5Okzh7xCyC7n85T+lyL0jREJDT434NMr6cAde7mLHmXDDkfptX1AfkjPk+B9lyRn0fFO01Z8r9SVrRGJAzLaL9CrJ/q4XvlnPBX5IT4/qyqqgJyFkWcX5v8/aXsyKSXKc7FLUBORuGHAeC7K18y5DjQ5CiOiBnU6T6zSjav9WWSPebcrV3qz2R4Tcnba85hyLTb9Le/nL2RY7fqsbLcnJdl30MOSeiwG9dzD4hX1DitnCoSBDlhpwy15VVRY9YDvxWhd/xYAjiF2ORLnYviG3+45dTDopcNbisftvvRrrjlQmzNAeCSLmStP9OSZR9KBx+6cK95LH0TPMC7S80UNGCRxMnbcA0kg8iiFEEhlkYh2Kg7vd/STvPj2Qy1NvKUO+PgCAEIQhBCEIQghAE53kdVfEUUHFYAAAAAElFTkSuQmCC");
      background-size: 52rpx;
      padding: 0 21rpx;
    }
    .container .header-bar input {
      flex: 1;
      height: 52rpx;
      border: 2rpx solid #e5e5e5;
      background: #fff;
      border-radius: 40rpx;
      padding: 0 20rpx;
      font-size: 30rpx;
    }
    .container .header-bar .icon-search {
      width: 62.5rpx;
      height: 62.5rpx;
      background: no-repeat center url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAQAAAD/5HvMAAAEx0lEQVQYGe3Bf0yUdRwH8I9GpBtZVpul0y1/ZD8sKzdXbupMh3Pq0jWtzbVs9YfL8scfLq02h1m52R3c832+z/d5HrjjAOH4KQhy4MQD4eS4gXiCePLjBIwU8VeCOAPy3dZf/mEpz56zW93rRRQVFRUVFfU/dGFM+UTHlOrXzq/yf9HwefeS0plpk4/F0b+je5x/UZXIPZV+URmRwMEhQfs940K+ry6hYTY9Wu0Tyze6yxVYwSGgQoUKFSpUCMiwwH6zPLVqZVcsPRrlSwvqVVghwMGhQYMOHTp0aNDAIcBhhQ53UcWLFH4127QrElQwqEi7keUu21W/vnl5+/y2dwKraj8p3pdZ7bzDIYNDQmqweQWFU/cTpU4GAQUMro6SbR2z6D4aFuRb0m4yqFCgDXq3U7hciynOSYQOBertgr2np9I/ODHPlSlDg4AN3m8oPKq+t0GHguSexg/ogepjPbvZkIACbci3lsx3Yr06rECGvSO4gB6SbxMb5pBhDwZeInN1vWJvY5DB+5uX0ShUfmeDAhtKCkOxZCZPogUCMo5vpFEJxRSkcKiQ0BBP5gnMSu+RIaGokEatc2ZqSEBCqasnhszi32SFgBYKLiQDqnfI0CAGz79B5uibkOOVIZCXTob0TrK3qeA4tpfM0TmPQYO427CBDHLrDAoO+H+LITM0r+VQkRy88DwZFFiXBAWOS73PkRl8WzgU5JVVjyeDQi+LPhmOW63zyAxH9yvgKE31jCGDKqZltTPYh+rXkBmKXAIyKpLIsJpn8hskpMDzJZmhKFuAoXIfGeaPO+i1IQXHtpIZPHsVyCgXZJhnUm6TBPtI3UdkBv9mDo5DOVUxZFDpjAO/yHDcCcSTGVreZxDI8F58kgxqelMe5LD3h+aQGbrnsBENYrDjbTKobnMSFLh8A7Fkhpa4Ao8MgcpdZEjTuAI3h4DnRzJLYEMiODKPX3qKDAjOF30a+N3gYjJLz+SMs0lQUL2ZDDiYqkDCQffFcWSeih8sYEht/HUqjVJgjehTIOH0CjJT99QDbRJsKCxtG0+j0PWqvUOGFYdzyGxnlyVf5ZCQ9xM9tJPP5jbaIMEZ7J5B5jv6FR/iUPsP778eRw+hc4ajhEGBs+NkPIXDmTFuRyI4FBSW9EyhB2h9N+O0AgEFR5MoXK49XilzMDBktBZ+Fnia/oZ/ev6elKscAioUOEPtCyl8POucfRwSZOTVunZWxg9MoHtcnuxek5mQE7JBhoAODQIStBttCyh8OubmHEke4LBAhXM4uykt35mWb8212bPSi7M6nX9wWCGQfL2M9U73JjBw2KBfbl1M4VPxmG9tdl76gA0WWCBBhQYNKiRY8TMYMnuzXdVL6S/H90hQwGHvObeEwiv4Vpn1UG1ea9ZV510dOhxIG8npOnykNKF5Lt2jZjeDCgXJl4PLKdx6xja+4Hm94D3Hh471rhXFi+qm0X3UfMsgwKDeOreUIoP3awYFEsTNs8soMnh3MnAw6FdallNkOLGLQUBBcl/LSooMtTtkqODQBlpWU2TwbZGhgEG5fWY1RQbfVhkcDKK/eTVFhtrtMjg49Butiygy+LfKEOAodlKkCHyq94vhUx9T5GiYXjn73FiKioqKior6z/oTCs8KMOW0P6QAAAAASUVORK5CYII=");
      background-size: 62.5rpx;
      padding: 0 21rpx;
    }
    .container .main-container {
      padding: 0 31.2rpx;
    }
    .container .main-container .hot-container .title {
      padding: 20rpx 0;
      font-size: 26rpx;
    }
    .container .main-container .hot-container >image {
      width: 100%;
      height: 208rpx;
      margin-bottom: 20rpx;
    }
    .container .main-container .hot-container .list {
      display: flex;
      flex-wrap: wrap;
    }
    .container .main-container .hot-container .list .item {
      padding: 14rpx 21rpx;
      font-size: 26rpx;
      border: 2rpx solid #e4e4e4;
      margin-right: 20rpx;
      margin-bottom: 20rpx;
    }
    .container .main-container .hot-container .list .item:nth-child(2n+1) {
      border-color: #e3af96;
      background: #fae8e8;
    }
    .container .main-container .hot-container .list .item:nth-child(2n+2) {
      border-color: #bbd090;
      background: #f2f6e9;
    }
    .container .main-container .hot-container .list .item:nth-child(2n+3) {
      border-color: #fac288;
      background: #f8f2ec;
    }
    .container .main-container .hot-container .list .item:nth-child(2n+4) {
      border-color: #fca0a7;
      background: #f9eaea;
    }
    .container .main-container .common-container .title {
      padding: 20rpx 0;
      font-size: 26rpx;
    }
    .container .main-container .common-container .list {
      display: flex;
      flex-wrap: wrap;
    }
    .container .main-container .common-container .list .item {
      padding: 14rpx 18rpx;
      font-size: 24rpx;
      background: #f5f5f5;
      color: rgba(0,0,0,0.54);
      margin-right: 14rpx;
      margin-bottom: 10rpx;
    }

</style>
