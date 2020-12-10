<template>
	<view class="">
		<swiper indicator-dots autoplay :interval="3000" :duration="1000" circular="">
			<block v-for="(item,index) in resdata" :key="index">
				<swiper-item>
					<view class="swiper-item" @tap="linkPage(item)">
						<image :src="item.picture" lazy-load mode="" class="banner-pic"></image>
					</view>
				</swiper-item>
			</block>
		</swiper>
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

<style>
	.banner-pic{height: 350upx;}
</style>
