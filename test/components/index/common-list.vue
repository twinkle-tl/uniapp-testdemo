<template>
	<view class="row">
		<block v-for="(item,index) in resdata" :key="index">
			<view class="span-4 d-flex flex-column j-center a-center py-1" @tap="linkPage(item)">
				<image :src="item.src" mode="widthFix" class="navImg"></image>
				<text>{{item.name}}</text>
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
