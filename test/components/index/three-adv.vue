<template>
	<view class="d-flex">
		<image :src="resdata.big.src" mode="" class="lad" @tap="linkPage(resdata.big)"></image>
		<view class="d-flex flex-column">
			<image :src="resdata.smalltop.src" mode="" class="rtad"></image>
			<image :src="resdata.smallbottom.src" mode="" class="rbad"></image>
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

<style>
	.lad{
		width: 373upx;height: 530upx;border-right: 2upx solid #f5f5f5;
	}
	.rtad{
		width: 375upx;height: 264upx;border-bottom: 2upx solid #f5f5f5;
	}
	.rbad{
		width: 375upx;height: 264upx;
	}
</style>
