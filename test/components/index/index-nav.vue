<template>
	<view class="row">
		<block v-for="(item,index) in resdata" :key="index">
			<view class="span-4 d-flex flex-column j-center a-center py-2" @tap="linkPage(item)">
				<image :src="item.src" mode="widthFix" class="navImg"></image>
				<text>{{item.text}}</text>
			</view>
		</block>
	</view>
</template>

<script>
	export default{
		props:{
			resdata: Array
		},
		methods:{
			linkPage(obj){
				switch(obj.text){
					case "特卖":
						uni.navigateTo({
							url: '../../pages/article/article'
						})
						break;
					case "商城":
						uni.navigateTo({
							url: '../../pages/mall/mall'
						})
						break;
				}
			}
		}
	}
</script>

<style scoped>
	.navImg{
		width: 60upx;
		height: 60upx;
	}
</style>
