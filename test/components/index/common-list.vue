<template>
	<view class="flex-1 list-box">
		<image :src="resdata.cover" mode="widthFix" class="list-img"></image>
		<view class="p-1">
			{{resdata.title}}
		</view>
		<view v-if="resdata.pprice" class="p-1">
			{{resdata.pprice}}
		</view>
		<view v-if="resdata.oprice" class="p-1">
			{{resdata.oprice}}
		</view>
		<view v-if="resdata.desc" class="p-1">
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
	.list-box{background-color: #f1f1f1; border-radius: 10upx;margin-bottom: 20upx;}
	.list-img{width: 362upx; border-radius: 10upx;}
</style>
