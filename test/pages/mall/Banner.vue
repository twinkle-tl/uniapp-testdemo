<template>
	<view>
		<swiper class="banner-container"
        :indicator-dots="true" 
        :autoplay="true" 
        :duration="1000" 
        indicator-color="#fff3"
        indicator-active-color="#fff">
		    <swiper-item class="swiper">
		        <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/b652ea15897d769e799665946966d51d.jpg?thumb=1&w=720&h=360" mode=""></image>
		    </swiper-item>
		    <swiper-item>
		        <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/68caca6f6cda76280dabe48ca92f23a7.jpg?thumb=1&w=720&h=360" mode=""></image>
		    </swiper-item>
		    <swiper-item>
		        <image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/2bea16c2f81cb22867afeae3e7467a92.jpg?thumb=1&w=720&h=360" mode=""></image>
		    </swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
        name:'HomeBanner',
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
    .banner-container {
      height: 375rpx;
      background-color: #ccc;
    }
    .banner-container image {
      width: 100%;
      height: 100%;
    }
</style>
