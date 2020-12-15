<template>
	<view>
		<view class="icons-container">
            <view class="item" v-for="(item,index) of list" :key="index">
                <image :src="item.imgUrl" mode=""></image>
            </view>
        </view>
	</view>
</template>

<script>
	export default {
        name:"HomeIcons",
		data() {
			return {
				list:[
                    {
                        title:'小米秒杀',
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/cb65daec7ef7b52cc785f88f78efba37.png?thumb=1&w=144&h=152'
                    },{
                        imgUrl:'https://i8.mifile.cn/v1/a1/eb5024fe-dfe3-6e53-3e18-675bef5fa06e.webp'
                    },{
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/9574184ec2dba1b314434c5a7cbd8bcd.jpg?thumb=1&w=144&h=152'
                    },{
                        imgUrl:'https://i8.mifile.cn/v1/a1/e8bc849a-0a3b-21a0-6810-7da3a3903dee.webp'
                    },{
                        imgUrl:'https://i8.mifile.cn/v1/a1/7dbcbf87-6a58-adb6-2f3f-bb3dae3e9c80.webp'
                    },{
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/bc1c677a6e10e42d00fb0a063662fbf9.png?thumb=1&w=144&h=152'
                    },{
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/9ea68dee2bfa0e55a82236b0d968e975.png?thumb=1&w=144&h=152'
                    },{
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/96c780016ea196743905dc93f9249c39.png?thumb=1&w=144&h=152'
                    },{
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/9425031cdd7af22d9a23a5ae16d1f57c.jpg?thumb=1&w=144&h=152'
                    },{
                        imgUrl:'https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/f11f9df6b0b0b428f8c8fc3267131830.png?thumb=1&w=144&h=152'
                    }
                ]
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
    .icons-container {
      display: flex;
      flex-wrap: wrap;
      margin-bottom: 16rpx;
    }
    .icons-container .item {
      width: 20%;
      height: 158.32rpx;
    }
    .icons-container .item image {
      width: 100%;
      height: 100%;
    }

</style>
