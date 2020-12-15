<template>
	<view class="content">
		<view class="header-bar">
            <!-- 搜索栏 -->
                <view class="search-bar">
                    <view class="icon-logo"></view>
                    <navigator class="input-wrap" url="../search/search">
                        <view class="icon-search"></view>
                        <input disabled type="text" placeholder="搜索商品名称" placeholder-class="input-placeholder" />
                    </navigator>
                    <!-- #ifdef H5 || APP-PLUS || MP-WEIXIN -->
                    <navigator open-type="switchTab" url="../my/my">
                        <image class="icon-user" src="../../static/tabbar/icon-user.23496a0116.png" mode=""></image>
                    </navigator>
                    <!-- #endif -->
                </view>
            <!-- 导航栏 -->
            <view class="nav-bar">
                <view @click="showDefaultNav=!showDefaultNav" class="nav-display">
                    <view class="icon-display" :class="{unfold:!showDefaultNav}"></view>
                </view>
                <view v-show="showDefaultNav" class="default-nav flex-row">
                    <view class="nav-item" 
                        v-for="(item,index) of navArr" 
                        @click="handleClickNav(item)"
                        :class="{active:currentNav==item}"
                        :key="index"><view>{{item}}</view></view>
                </view>
                <view v-show="!showDefaultNav" class="all-nav">
                    <view class="title">全部</view>
                    <view class="nav-container">
                        <view class="nav-item"
                            v-for="(item,index) of navArr" 
                            @click="handleClickNav(item)"
                            :class="{active:currentNav==item}"
                            :key="index">{{item}}</view>
                    </view>
                </view>
            </view>
        </view>
        <view @click="showDefaultNav=true" v-show="!showDefaultNav" class="mask"></view>
	</view>
</template>

<script>
	export default {
        name:'HomeHeader',
		data() {
			return {
				navArr:['推荐','手机','智能','电视','笔记本','家电','生活周边'],
                showDefaultNav:true,
                currentNav:'推荐'
			}
		},
        watch:{
            currentNav(val){
                // console.log(val);
                this.$emit('navChange',val)
            }
        },
		onLoad() {

		},
		methods: {
            handleClickNav(nav){
                console.log(11);
                this.currentNav = nav
            }
		}
	}
</script>

<style scoped>
    .content {
      padding-top: calc(var(--status-bar-height) + 147.5rpx);
    }
    .content .header-bar {
      position: fixed;
      z-index: 10;
      top: 0;
      width: 100%;
      background: #f2f2f2;
    }
    .content .header-bar .search-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 87.5rpx;
    }
    .content .header-bar .search-bar .icon-logo {
      width: 50rpx;
      height: 32rpx;
      margin: 0 26rpx;
      background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEwAAAAyCAYAAAD2vz2aAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyhpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTM4IDc5LjE1OTgyNCwgMjAxNi8wOS8xNC0wMTowOTowMSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTcgKE1hY2ludG9zaCkiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MjQ2OUE2MkU0RTQ4MTFFNzgxOTZBRDJFQjk4Qjk0NjQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MjQ2OUE2MkY0RTQ4MTFFNzgxOTZBRDJFQjk4Qjk0NjQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDpCOUQ0QkM2RjREQ0MxMUU3ODE5NkFEMkVCOThCOTQ2NCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDpCOUQ0QkM3MDREQ0MxMUU3ODE5NkFEMkVCOThCOTQ2NCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PiL8gcIAAAF1SURBVHja7Ju/LwRRFEbf+FVsQ0dBdJKNSksUSqVCr6AhKxGVwn+gVUpQEI1So5XoZUOhEbKMDiESIeOTzPbvzpoxz5wvOd3duzsn++7cSXajZMU9OOeGXPmTiHtxIU7FoYh/oe+ZmPKsjSMJS1yY+RS7YrNDcTdi1Le4y4WbHrEorsRcUW8asrB2BsSxWEeYLVtiCWG2bIsJhPmnV+zkeV3/TZhLv2HzCLNlFWG2TIqRvHYZa97FR84XXEvnUSeZEft/LexZDIvXnIVFop6uCQ3RnaHHeBmO5FMBstrPjZdiTUyLlww9Bqs6w87FcobX9Vd56B+IZoZjXVlhP0f0qAwfJKS1ookw+w0HYaEFYQVs+j4ZE7Oed6o3sVfA00OphW2IBUN9S5xU+Uhad6A+ZhhDnyAMYQhDGMIQRhCGMIQhDGEEYQhDGMIQhjCCMIQhDGEIIwhDWFHCLP81vPOsezT0/BK3nj0tP1i59qxrGXrG3wIMAK5yNsqRAjAyAAAAAElFTkSuQmCC");
      background-size: cover;
    }
    .content .header-bar .search-bar .input-wrap {
      position: relative;
      flex: 1;
      padding-right: 200rpx;
      box-sizing: border-box;
    }
    .content .header-bar .search-bar .input-wrap .icon-search {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      left: 12rpx;
      width: 42rpx;
      height: 42rpx;
      background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAQAAAD/5HvMAAAEx0lEQVQYGe3Bf0yUdRwH8I9GpBtZVpul0y1/ZD8sKzdXbupMh3Pq0jWtzbVs9YfL8scfLq02h1m52R3c832+z/d5HrjjAOH4KQhy4MQD4eS4gXiCePLjBIwU8VeCOAPy3dZf/mEpz56zW93rRRQVFRUVFfU/dGFM+UTHlOrXzq/yf9HwefeS0plpk4/F0b+je5x/UZXIPZV+URmRwMEhQfs940K+ry6hYTY9Wu0Tyze6yxVYwSGgQoUKFSpUCMiwwH6zPLVqZVcsPRrlSwvqVVghwMGhQYMOHTp0aNDAIcBhhQ53UcWLFH4127QrElQwqEi7keUu21W/vnl5+/y2dwKraj8p3pdZ7bzDIYNDQmqweQWFU/cTpU4GAQUMro6SbR2z6D4aFuRb0m4yqFCgDXq3U7hciynOSYQOBertgr2np9I/ODHPlSlDg4AN3m8oPKq+t0GHguSexg/ogepjPbvZkIACbci3lsx3Yr06rECGvSO4gB6SbxMb5pBhDwZeInN1vWJvY5DB+5uX0ShUfmeDAhtKCkOxZCZPogUCMo5vpFEJxRSkcKiQ0BBP5gnMSu+RIaGokEatc2ZqSEBCqasnhszi32SFgBYKLiQDqnfI0CAGz79B5uibkOOVIZCXTob0TrK3qeA4tpfM0TmPQYO427CBDHLrDAoO+H+LITM0r+VQkRy88DwZFFiXBAWOS73PkRl8WzgU5JVVjyeDQi+LPhmOW63zyAxH9yvgKE31jCGDKqZltTPYh+rXkBmKXAIyKpLIsJpn8hskpMDzJZmhKFuAoXIfGeaPO+i1IQXHtpIZPHsVyCgXZJhnUm6TBPtI3UdkBv9mDo5DOVUxZFDpjAO/yHDcCcSTGVreZxDI8F58kgxqelMe5LD3h+aQGbrnsBENYrDjbTKobnMSFLh8A7Fkhpa4Ao8MgcpdZEjTuAI3h4DnRzJLYEMiODKPX3qKDAjOF30a+N3gYjJLz+SMs0lQUL2ZDDiYqkDCQffFcWSeih8sYEht/HUqjVJgjehTIOH0CjJT99QDbRJsKCxtG0+j0PWqvUOGFYdzyGxnlyVf5ZCQ9xM9tJPP5jbaIMEZ7J5B5jv6FR/iUPsP778eRw+hc4ajhEGBs+NkPIXDmTFuRyI4FBSW9EyhB2h9N+O0AgEFR5MoXK49XilzMDBktBZ+Fnia/oZ/ev6elKscAioUOEPtCyl8POucfRwSZOTVunZWxg9MoHtcnuxek5mQE7JBhoAODQIStBttCyh8OubmHEke4LBAhXM4uykt35mWb8212bPSi7M6nX9wWCGQfL2M9U73JjBw2KBfbl1M4VPxmG9tdl76gA0WWCBBhQYNKiRY8TMYMnuzXdVL6S/H90hQwGHvObeEwiv4Vpn1UG1ea9ZV510dOhxIG8npOnykNKF5Lt2jZjeDCgXJl4PLKdx6xja+4Hm94D3Hh471rhXFi+qm0X3UfMsgwKDeOreUIoP3awYFEsTNs8soMnh3MnAw6FdallNkOLGLQUBBcl/LSooMtTtkqODQBlpWU2TwbZGhgEG5fWY1RQbfVhkcDKK/eTVFhtrtMjg49Butiygy+LfKEOAodlKkCHyq94vhUx9T5GiYXjn73FiKioqKior6z/oTCs8KMOW0P6QAAAAASUVORK5CYII=");
      background-size: cover;
    }
    .content .header-bar .search-bar .input-wrap input {
      height: 66.5rpx;
      background: #fff;
      border: 2rpx solid #e5e5e5;
      padding-left: 62.5rpx;
      border-radius: 80rpx;
    }
    .content .header-bar .search-bar .input-wrap input .input-placeholder {
      color: rgba(0,0,0,0.3);
    }
    .content .header-bar .search-bar .icon-user {
      width: 42rpx;
      height: 42rpx;
      margin: 8rpx 32rpx 0;
    }
    .content .header-bar .nav-bar {
      position: relative;
    }
    .content .header-bar .nav-bar .nav-display {
      position: absolute;
      right: 0;
      top: 0;
      width: 70rpx;
      height: 57rpx;
      box-sizing: border-box;
      padding-left: 12rpx;
      padding-top: 12rpx;
      background: #f2f2f2;
      box-shadow: -15rpx 0 15rpx 0 #f2f2f2;
    }
    .content .header-bar .nav-bar .nav-display .icon-display {
      width: 41.66rpx;
      height: 41.66rpx;
      background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAMAAABiM0N1AAAABlBMVEX///+9vb18/6H5AAAAAXRSTlMAQObYZgAAAF9JREFUeNrtzCESwDAMxMD4/59umIBJJ6JalLo3OkmS5Ie55IbRyAmrUQtmlxisoeswtR3GurPn+4crcXYljq7EyZU4uBKfrsSHK/F0JR6mhCPYDmwHdKzVUaWTJElefOyLAQtGqMZ7AAAAAElFTkSuQmCC");
      background-size: cover;
      transition: transform 0.2s linear;
    }
    .content .header-bar .nav-bar .nav-display .icon-display.unfold {
      transform: rotate(180deg);
    }
    .content .header-bar .nav-bar .default-nav {
      height: 60rpx;
      padding-right: 79rpx;
      overflow-x: auto;
      white-space: nowrap;
      font-size: 28rpx;
      color: #747474;
    }
    .content .header-bar .nav-bar .default-nav::-webkit-scrollbar {
      height: 0;
      background: transparent;
    }
    .content .header-bar .nav-bar .default-nav .nav-item {
      padding: 0 26rpx;
    }
    .content .header-bar .nav-bar .default-nav .nav-item>view {
      height: 60rpx;
      line-height: 60rpx;
      box-sizing: border-box;
    }
    .content .header-bar .nav-bar .default-nav .nav-item.active>view {
      color: #ed5b00;
      border-bottom: 4rpx solid #ed5b00;
    }
    .content .header-bar .nav-bar .all-nav {
      padding: 26rpx 26rpx 0;
    }
    .content .header-bar .nav-bar .all-nav .nav-container {
      padding-top: 35.4rpx;
      justify-content: space-between;
      display: flex;
      flex-wrap: wrap;
    }
    .content .header-bar .nav-bar .all-nav .nav-container:after {
      width: 154rpx;
      display: block;
      height: 0;
      content: '';
    }
    .content .header-bar .nav-bar .all-nav .nav-container .nav-item {
      width: 154rpx;
      height: 54rpx;
      margin-bottom: 25rpx;
      line-height: 54rpx;
      text-align: center;
      background: #fff;
      border: 1px solid #e5e5e5;
      border-radius: 8rpx;
    }
    .content .header-bar .nav-bar .all-nav .nav-container .nav-item.active {
      background-color: #fde0d5;
      border-color: #ff6700;
      color: #ff6700;
    }                           
</style>
