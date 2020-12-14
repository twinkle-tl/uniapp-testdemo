<template>
	<view class="list-box">
		<image :src="resdata.cover" mode="widthFix" class="list-img"></image>
		<view class="p-1 title">
			{{resdata.title}}
		</view>
		<view v-if="resdata.pprice" class="px-1">
			<text class="pprice">￥{{resdata.pprice}}</text>
			<text class="oprice">￥{{resdata.oprice}}</text>
		</view>
		<view v-if="resdata.desc" class="p-1 desc">
			{{resdata.desc}}
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			resdata: Object
		},
		methods:{
			linkPage(obj){
				
			}
		}
	}
</script>

<style scoped>
	.list-box{border: 1upx solid #f1f1f1; border-radius: 10upx;margin-bottom: 10upx;box-shadow: 2upx 6upx 6upx #f1f1f1;flex: 1;
	background-color: #fff;width: 362upx;break-inside: avoid;}
	.list-img{border-radius: 10upx 10upx 0 0;}
	.title{height: 84upx;text-overflow: ellipsis;display: -webkit-box;-webkit-box-orient: vertical; -webkit-line-clamp: 2; overflow: hidden;}
	.pprice{color: #f00}
	.oprice{color: #666;font-size: 12px;text-decoration: line-through;padding-left: 10upx;}
	.desc{color: #666;font-size: 12px;}
</style>
