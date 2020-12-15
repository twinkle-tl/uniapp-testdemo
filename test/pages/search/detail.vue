<template>
	<view class="container">
		<view class="header-bar">
            <view class="search-bar flex-row">
                <navigator class="icon-back" open-type="navigateBack"></navigator>
                <input type="text" placeholder="搜索商品名称" />
                <navigator class="icon-search" url="./detail"></navigator>
            </view>
            <view class="sort-bar flex-row">
                <view @click="showChildSort=!showChildSort" :class="{active:currentSort==currentFirstSort}" class="sum">
                    <text>{{currentFirstSort}}</text>
                </view>
                <view @click="handleClickSort('销量')" :class="{active:currentSort=='销量'}"><text>销量</text></view>
                <view :class="{upActive:currentSort=='up',downActive:currentSort=='down'}" class="price">
                    <text>价格</text>
                    <view @click="handleClickSort('up')" class="up"></view>
                    <view @click="handleClickSort('down')" class="down"></view>
                </view>
                <view><text>筛选</text></view>
            </view>
            <view v-show="showChildSort" class="child-sort">
                <view @click="handleClickFirstSort('综合')" :class="{active:currentSort=='综合'}">综合排序</view>
                <view @click="handleClickFirstSort('新品')" :class="{active:currentSort=='新品'}">新品优先</view>
            </view>
        </view>
        <view>hhhhhhhhhhhhh</view>
        <view @click="showChildSort=false" v-show="showChildSort" class="mask"></view>
	</view>
</template> 

<script>
export default {
    data() {
        return {
            sortNav:[
                {name:'综合',active:true,child:[
                    {name:'综合排序',active:true},
                    {name:'新品优先',active:false}
                ]},
                {name:'销量',active:false},
                {name:'价格',active:false},
                {name:'筛选',active:false},
            ],
            currentSort: '综合',
            currentFirstSort:'综合',
            showChildSort:false,
        }
    },
    methods: {
        handleClickSort(sortType){
            console.log(sortType);
            this.currentSort = sortType;
            this.showChildSort = false;
            if(sortType == '销量'){
                // do 排序
            }else if(sortType == 'up'){
                // 
            }else if(sortType == 'down'){
                // 
            }
        },
        handleClickFirstSort(sortType){
            this.currentFirstSort = sortType;
            this.currentSort = sortType;
            this.showChildSort = false;
            if(sortType == '综合'){
                // 
            }else if(sortType == '新品'){
                // 
            }
            
        }
            
    }
}
</script>

<style scoped>
    .container {
      padding-top: calc(var(--status-bar-height) + 160rpx);
    }
	
	.header-bar {
	  position: fixed;
	  z-index: 99;
	  top: var(--status-bar-height);
	  width: 100%;
	  height: 160rpx;
	  background: #fafafa;
	}

	
	.search-bar {
	  height: 82rpx;
	}
	.search-bar .icon-back {
	  width: 52rpx;
	  height: 52rpx;
	  background: no-repeat center url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAYAAABV7bNHAAABfUlEQVR4AWL4//8/oH1zzA4gCMJgbNv239i2beP+R8gXczpmV79XB9ja3UEDDJCAIAQhCEF/TBAgCEEIUkSKFrEoahD0VFCdOLtmWxQh6E5Okzh7xCyC7n85T+lyL0jREJDT434NMr6cAde7mLHmXDDkfptX1AfkjPk+B9lyRn0fFO01Z8r9SVrRGJAzLaL9CrJ/q4XvlnPBX5IT4/qyqqgJyFkWcX5v8/aXsyKSXKc7FLUBORuGHAeC7K18y5DjQ5CiOiBnU6T6zSjav9WWSPebcrV3qz2R4Tcnba85hyLTb9Le/nL2RY7fqsbLcnJdl30MOSeiwG9dzD4hX1DitnCoSBDlhpwy15VVRY9YDvxWhd/xYAjiF2ORLnYviG3+45dTDopcNbisftvvRrrjlQmzNAeCSLmStP9OSZR9KBx+6cK95LH0TPMC7S80UNGCRxMnbcA0kg8iiFEEhlkYh2Kg7vd/STvPj2Qy1NvKUO+PgCAEIQhBCEIQghAE53kdVfEUUHFYAAAAAElFTkSuQmCC");
	  background-size: 52rpx;
	  padding: 0 21rpx;
	}
	.search-bar input {
	  flex: 1;
	  height: 52rpx;
	  border: 2rpx solid #e5e5e5;
	  background: #fff;
	  border-radius: 4rpx;
	  padding: 0 20rpx;
	  font-size: 30rpx;
	}
	.search-bar .icon-search {
	  width: 62.5rpx;
	  height: 62.5rpx;
	  background: no-repeat center url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAQAAAD/5HvMAAAEx0lEQVQYGe3Bf0yUdRwH8I9GpBtZVpul0y1/ZD8sKzdXbupMh3Pq0jWtzbVs9YfL8scfLq02h1m52R3c832+z/d5HrjjAOH4KQhy4MQD4eS4gXiCePLjBIwU8VeCOAPy3dZf/mEpz56zW93rRRQVFRUVFfU/dGFM+UTHlOrXzq/yf9HwefeS0plpk4/F0b+je5x/UZXIPZV+URmRwMEhQfs940K+ry6hYTY9Wu0Tyze6yxVYwSGgQoUKFSpUCMiwwH6zPLVqZVcsPRrlSwvqVVghwMGhQYMOHTp0aNDAIcBhhQ53UcWLFH4127QrElQwqEi7keUu21W/vnl5+/y2dwKraj8p3pdZ7bzDIYNDQmqweQWFU/cTpU4GAQUMro6SbR2z6D4aFuRb0m4yqFCgDXq3U7hciynOSYQOBertgr2np9I/ODHPlSlDg4AN3m8oPKq+t0GHguSexg/ogepjPbvZkIACbci3lsx3Yr06rECGvSO4gB6SbxMb5pBhDwZeInN1vWJvY5DB+5uX0ShUfmeDAhtKCkOxZCZPogUCMo5vpFEJxRSkcKiQ0BBP5gnMSu+RIaGokEatc2ZqSEBCqasnhszi32SFgBYKLiQDqnfI0CAGz79B5uibkOOVIZCXTob0TrK3qeA4tpfM0TmPQYO427CBDHLrDAoO+H+LITM0r+VQkRy88DwZFFiXBAWOS73PkRl8WzgU5JVVjyeDQi+LPhmOW63zyAxH9yvgKE31jCGDKqZltTPYh+rXkBmKXAIyKpLIsJpn8hskpMDzJZmhKFuAoXIfGeaPO+i1IQXHtpIZPHsVyCgXZJhnUm6TBPtI3UdkBv9mDo5DOVUxZFDpjAO/yHDcCcSTGVreZxDI8F58kgxqelMe5LD3h+aQGbrnsBENYrDjbTKobnMSFLh8A7Fkhpa4Ao8MgcpdZEjTuAI3h4DnRzJLYEMiODKPX3qKDAjOF30a+N3gYjJLz+SMs0lQUL2ZDDiYqkDCQffFcWSeih8sYEht/HUqjVJgjehTIOH0CjJT99QDbRJsKCxtG0+j0PWqvUOGFYdzyGxnlyVf5ZCQ9xM9tJPP5jbaIMEZ7J5B5jv6FR/iUPsP778eRw+hc4ajhEGBs+NkPIXDmTFuRyI4FBSW9EyhB2h9N+O0AgEFR5MoXK49XilzMDBktBZ+Fnia/oZ/ev6elKscAioUOEPtCyl8POucfRwSZOTVunZWxg9MoHtcnuxek5mQE7JBhoAODQIStBttCyh8OubmHEke4LBAhXM4uykt35mWb8212bPSi7M6nX9wWCGQfL2M9U73JjBw2KBfbl1M4VPxmG9tdl76gA0WWCBBhQYNKiRY8TMYMnuzXdVL6S/H90hQwGHvObeEwiv4Vpn1UG1ea9ZV510dOhxIG8npOnykNKF5Lt2jZjeDCgXJl4PLKdx6xja+4Hm94D3Hh471rhXFi+qm0X3UfMsgwKDeOreUIoP3awYFEsTNs8soMnh3MnAw6FdallNkOLGLQUBBcl/LSooMtTtkqODQBlpWU2TwbZGhgEG5fWY1RQbfVhkcDKK/eTVFhtrtMjg49Butiygy+LfKEOAodlKkCHyq94vhUx9T5GiYXjn73FiKioqKior6z/oTCs8KMOW0P6QAAAAASUVORK5CYII=");
	  background-size: 62.5rpx;
	  padding: 0 21rpx;
	}
	
	.child-sort {
	  background: #fafafa;
	}
	.child-sort >view {
	  height: 100rpx;
	  line-height: 100rpx;
	  margin: 0 34rpx;
	  font-size: 30rpx;
	  color: rgba(0,0,0,0.871);
	  border-bottom: 2rpx solid rgba(0,0,0,0.15);
	}
	.child-sort >view.active {
	  color: #ff6700;
	  position: relative;
	}
	.child-sort >view.active:after {
	  position: absolute;
	  content: "";
	  right: 10rpx;
	  top: 50%;
	  transform: translateY(-50%);
	  width: 36rpx;
	  height: 24rpx;
	  background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACQAAAAYCAYAAACSuF9OAAAAAXNSR0IArs4c6QAAAWJJREFUSA3F1r9KxEAQBvBvAmoh9wD2Vr6C+gTXWSgi2OoJNqKdwnFvYOc9wjV2YqGFnaWF7fVqKXYirt/cwZIjidlshs1A/uxmd+dHsptE0HG4AS7gcEbGM5awL1163DFGxFx5Q4bdzBcSnxQwgl/ipp2AChiQApzIDV6SP7JSjGBAzFgfUlJQHSYpKASTDBSKUZCf1O4cq1phHU0wmlvcKVbwjUeeb3GbYA2HMmSNQTTFaMoMP9jmUTEae3jDrRtieV6M38dgNFvG1K88fuZS99uiYjEzkFzjg4u/z8KXBaoNRvP79xAH2uT78p51vRzsjnNqJ3ROtcUsgLTQBmWBKYBiUVaYUlBTlCWmEhSKssb8C6pD4R2XCz9X+guR+2pr/5jwq6yqM+9CcfUJpky/nutjgtHxakHaqBSlF+ZhhtHhgkDasAJlimkEKkGZYxqDZqgjbPC+HnAOPckYD1pnGX+3u8d2kq5oywAAAABJRU5ErkJggg==") 50% 0;
	  background-size: cover;
	}
	
	.sort-bar {
	  height: 78rpx;
	}
	.sort-bar >view {
	  width: 25%;
	  height: 78rpx;
	  line-height: 78rpx;
	  text-align: center;
	  color: rgba(0,0,0,0.54);
	  font-size: 30rpx;
	}
	.sort-bar >view.active {
	  color: #ff6700;
	}
	.sort-bar .sum text {
	  position: relative;
	}
	.sort-bar .sum text:after {
	  content: "";
	  position: absolute;
	  top: 50%;
	  right: -24rpx;
	  width: 0;
	  height: 0;
	  border: 8rpx solid;
	  border-color: #bdbdbd transparent transparent;
	}
	.sort-bar .sum.active text:after {
	  border-top-color: #ff6700;
	}
	.sort-bar .price {
	  position: relative;
	}
	.sort-bar .price .up {
	  position: absolute;
	  top: 0;
	  width: 100%;
	  height: 50%;
	}
	.sort-bar .price .down {
	  top: 50%;
	}
	.sort-bar .price text {
	  position: relative;
	}
	.sort-bar .price text:before,
	.sort-bar .price text:after {
	  content: "";
	  position: absolute;
	  right: -24rpx;
	  width: 0;
	  height: 0;
	  border: 8rpx solid;
	}
	.sort-bar .price text:before {
	  top: 0;
	  border-color: transparent transparent #bdbdbd;
	}
	.sort-bar .price text:after {
	  bottom: 0;
	  border-color: #bdbdbd transparent transparent;
	}
	.sort-bar .price.upActive,
	.sort-bar .price.downActive {
	  color: #ff6700;
	}
	.sort-bar .price.upActive text:before {
	  border-bottom-color: #ff6700;
	}
	.sort-bar .price.downActive text:after {
	  border-top-color: #ff6700;
	} 
</style>
