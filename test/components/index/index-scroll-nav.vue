<template>
	<view class="">
		<swiper :indicator-dots="false" :autoplay="false" :interval="3000" :duration="1000" @change="bannerfun">
			<block v-for="item,index in relist" :key="index">
				<swiper-item>
					<view class="swiper-item row">
						<block v-for="temp,index2 in item" :key="index2">
							<view class="span-4 d-flex flex-column j-center a-center py-2">
								<image :src="temp.src" mode="widthFix" class="navImg"></image>
								<text>{{temp.text}}</text>
							</view>
						</block>
					</view>
				</swiper-item>
			</block>
		</swiper>
		<view class="instruct-view">
			<block v-for="item,index in relist" :key="index">
				<view class="instruct" :class="{active: index==num}">
					
				</view>
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
			return {
				num:0,
				relist:[],
			}
		},
		mounted() {
			const _temp=this.resdata
			let i=0
			for (let i = 0; i < _temp.length; i += 10) {
			  this.relist.push(_temp.slice(i, i + 10)) // 每10项分成一组        
			}
		},
		methods:{
			linkPage(obj){
				switch(obj.text){
					case "资讯":
					uni.navigateTo({
						url: '../../pages/article/article'
					})
					break;
				}
			},
			bannerfun(e){
				this.num=e.detail.current
			}
		}
	}
</script>

<style scoped>
	.navImg{
		width: 60upx;
		height: 60upx;
	}
	/*指示点*/
	.instruct-view {
		display: flex;
		justify-content: center;
		padding-top: 10upx;
		padding-bottom: 10upx;
	}
	
	.instruct {
		background: #B2B2B2;
		height: 8upx;
		width: 30upx;
		border-radius: 50upx;
		margin: 0 8upx;
	}
	
	.active {
		background: #fbae22 !important;
	}
</style>
