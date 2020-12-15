<template>
	<view>
		<view class="header-bar">
            <image src="../../static/images/avatar.76a75b8f17.png" mode=""></image>
            <navigator url="../login/login">
                <text>登录/注册</text>
            </navigator>
        </view>
        <view class="order-row flex-row more-right">
            <text>我的订单</text>
            <text>全部订单</text>
        </view>
        <view class="service-row flex-row">
            <view class="item flex-col">
                <view class="icon"></view>
                <text>待付款</text>
            </view>
            <view class="item flex-col">
                <view class="icon"></view>
                <text>待收货</text>
            </view>
            <view class="item flex-col">
                <view class="icon"></view>
                <text>退换修</text>
            </view>
        </view>
        
        
	</view>
</template>

<script>
export default {
    name:"MyHeader",
    data() {
        return {
            
        }
    },
    methods: {
        
    },
}
</script>

<style scoped>
    .header-bar {
      display: flex;
      align-items: center;
      height: 166rpx;
      width: 100%;
      box-sizing: border-box;
      padding-left: 38rpx;
      background: url("https://m.mi.com/static/img/bg.63c8e19851.png") center #f37d0f;
      background-size: cover;
    }
    .header-bar image {
      width: 100rpx;
      height: 100rpx;
      overflow: hidden;
      box-sizing: border-box;
      border-radius: 100%;
      border: 3px solid rgba(255,255,255,0.4);
      text-align: center;
      margin-right: 17rpx;
    }
    .header-bar text {
      color: #fff;
      font-size: 26rpx;
    }
    .order-row {
      height: 81rpx;
      padding-left: 32rpx;
      background-color: #fff;
      border-bottom: 2rpx solid rgba(0,0,0,0.15);
    }
    .order-row text:nth-child(1) {
      font-size: 30rpx;
    }
    .service-row {
      height: 176rpx;
      padding: 0 83.2rpx;
      background-color: #fff;
      margin-bottom: 21rpx;
    }
    .service-row .item {
      font-size: 24rpx;
    }
    .service-row .item .icon {
      width: 50rpx;
      height: 50rpx;
      margin-bottom: 16rpx;
    }
    .service-row .item:nth-child(1) .icon {
      background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAYAAABV7bNHAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyppVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTMyIDc5LjE1OTI4NCwgMjAxNi8wNC8xOS0xMzoxMzo0MCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTUuNSAoTWFjaW50b3NoKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDpGMUQ5NDYxMThGQTkxMUU2OTNFMENEREQ1RkNGRDZCQyIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDpGMUQ5NDYxMjhGQTkxMUU2OTNFMENEREQ1RkNGRDZCQyI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOkYxRDk0NjBGOEZBOTExRTY5M0UwQ0RERDVGQ0ZENkJDIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOkYxRDk0NjEwOEZBOTExRTY5M0UwQ0RERDVGQ0ZENkJDIi8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+0LK+9gAAAXNJREFUeNrsnLEOgjAURcUYd/k/Rhh1My7+gJsrYeP7xNHEpXZoIjYIpQnwaM9N3qBLw8nr7ePWmCilNui/tiAAEIAABCAAAQhAkWrX/lCWZXQAiqIY3UF7XXddD10qwGrM8+1Hd5DRTdcx4KY5mOd76br4eFAWye7KfU06jQRQ6rvFbCUBQRkdXXDMAwhAAAIQgAAEIAAh70k6aNkRjx1/SOugqaOWrleP3vhDWgctEbX0xh/SOmjJqCVfg0mn0taWbtJTRy2D8QfHPIAABKCBeWnUNU4sk7Q9Lzlf48TSQZnrHIMH4UGdqju+q/Cgr85miMxawK4A+uqt62SKLYYHAWi9ku5Big76VSNtbWmA6gXXrtawxdrzzWGmNZ99c5Q0QFPPN7anDSaW0d+L+fwMGAEIQAACEIAABCAAIadJWtFBDq/9AarxBVRHAqjy3WJLRA5zqjfecAE025XKGpTw9zgc8wACEIAABCAAAQh16SPAAD22hrFVOZLnAAAAAElFTkSuQmCC") no-repeat center 0;
      background-size: cover;
    }
    .service-row .item:nth-child(2) .icon {
      background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAYAAABV7bNHAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyppVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTMyIDc5LjE1OTI4NCwgMjAxNi8wNC8xOS0xMzoxMzo0MCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTUuNSAoTWFjaW50b3NoKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDpGMUQ5NDYxNThGQTkxMUU2OTNFMENEREQ1RkNGRDZCQyIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDpGMUQ5NDYxNjhGQTkxMUU2OTNFMENEREQ1RkNGRDZCQyI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOkYxRDk0NjEzOEZBOTExRTY5M0UwQ0RERDVGQ0ZENkJDIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOkYxRDk0NjE0OEZBOTExRTY5M0UwQ0RERDVGQ0ZENkJDIi8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+4cr/ZAAAA0JJREFUeNrsnD1oFEEUx+e8GLGQxFOw0MbCryhGEGyFoKIoCFqKoqKniGjSSBSuVRTRRBTMcYUQLBUbbSJpUlkIBpOIprG00IsEJOJH1v9jH7JZ5vb29nb25nbfgx9cZnbv7f13Pt68nU3OcRwlVtuWiQQiUFPWUS6XE3VYLBalBUkXE4HE/o9BSTtMesxrdmyUFtTiLtYJhsE34FhGla+ts5Vd7A64YmnjWM3XtgAGW9WCTrZBLzrfyi5WaAOBCjbNYjlLRAm9QpdZTAQSgUSgtAq0VgSqbUfBlAikj05HwQuwTlbzS+0gqID1MgYttVVgBLxKmzhxCLQXTIKiJkqezLJAy8FtMA42+ur+gJtgT1bHoC3gKditqZsBZ8GbrHaxc+CtRpxFcJfLUyNOIy1oDaBk8jFN3WdwCkxkNZLuA+9qiPME9KZVnHoCUa52CIyBDb66ryzYGTCf5rVYUBejfPJVTTnNXCfAl6wvVk9rpu8S2J8Vceq1oC7NWDShMmaNTPOZE8dkukMEEoHEGl6LOdKCzFpVBAq2Stq7WFSbU26eupR2gXIqg9ah23pm6zY5meZFIBFIBBKBmrMecA98AD+ZGS7raSMfsQtE6dmH4D0YAFvBCmYbl1HdY7DSYh9GAkW68JdgX4ibcQFsAofAL8t8GGtB90NcuNf6uDvY5sOIQNv5jnltFhxXbsq2iz/P+o65yOfa4sOYQPSkNe/5+5Nyn8k/V+7joHn+TGUfPcfl+VxbfMQikO59h37fMdfBd825VHbDV9avwr1TYcJHLAJFyd+8Dqgbi2liidtHNapAozGHFElkJKP4qEQV6Bp4wPmcsBY00xyISYS4fMzx7ytFFYhiCHr0XOBckI4h3zm0capb813dXOe14YDvTcJHgX9fYKyUi/qfFzhntEO5Oz/yvil40DMe0KPqW2Cz55i/YBeYCnpNPAkfpiNp2gtNGzgvecooin1W57wRFX4fdRI+jEbSA3VmFr+N8zm2+TAmEPXhw+CRcrfi1bJFvqtHIqyRkvBhdDVPF3MZ7OSBkSLa3+AHmOayXg7/Fyz2YWQ177VpTeSr2tBH87NYVkxSriKQCCQCiUAikAiUWvsnwABTSwDIZ7YMEAAAAABJRU5ErkJggg==") no-repeat center 0;
      background-size: cover;
    }
    .service-row .item:nth-child(3) .icon {
      background: url("../../static/images/nav-4.d68723895f.png") no-repeat center 0;
      background-size: cover;
    }
</style>
