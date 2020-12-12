<template>
	<view class="position-relative">
		<swiper :indicator-dots="false" autoplay :interval="3000" :duration="1000" @change="bannerfun">
			<block v-for="(item,index) in resdata" :key="index">
				<swiper-item>
					<view class="swiper-item" @tap="linkPage(item)">
						<image :src="item.picture" lazy-load mode="" class="banner-pic"></image>
					</view>
				</swiper-item>
			</block>
		</swiper>
		<view class="dots">
			<block v-for="(item,index) in resdata" :key="index">
				<view class="dot-item" :class="{active: curindex==index}"></view>
			</block>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			resdata: Array
		},
		data(){
			return{
				curindex: 0,
			}
		},
		methods:{
			bannerfun(e){
				this.curindex=e.detail.current
			},
			linkPage(obj){
				
			}
		}
	}
</script>

<style>
	.banner-pic{height: 350upx;}
	.dots{position: absolute;bottom: 20upx;left: 43%;display: flex;height: 6upx;width: 100upx;border-radius: 6px;background-color: rgba(255,241,254,0.4);}
	.dot-item{height: 6upx;flex: 1;border-radius: 6px;}
	.dot-item.active{background-color: #fff;}
</style>
