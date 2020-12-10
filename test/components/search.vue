<template>
	<view class="">
		<view class="search-view">
			<image src="../static/location.png" mode="widthFix"></image>
			<text class="search-text">云南昆明</text>
			<text>></text>
		</view>
		<view class="search-cont">
			<view class="search" @click="search()">
				<image src="../static/extuiHL.png" mode="widthFix" class="search-img"></image>
				<input type="text" placeholder="关键词" disabled />			</view>
		</view>
		<view class="swiper-view">
			<swiper :indicator-dots="false" :autoplay="true" :interval="3000" :duration="1000" @change="bannerfun"> 
				<block v-for="item,index in label">
					<swiper-item>
						<view class="swiper-item">
							<block v-for="temp in item">
								<view class="conteng-img">
									<image src="../static/extuiHL.png" mode="widthFix" class="uploadimg"></image>
									<text>{{temp.text}}</text>
								</view>
							</block>
						</view>
					</swiper-item>
				</block>
			</swiper>
		</view>
		<view class="instruct-view">
			<block v-for="item,index in intructdata">
				<view class="instruct" :class="{active: index==num}">
					{{item}}
				</view>
			</block>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num:0,
				intructdata:['',''],
				label: [
					[{
							img: '1',
							text: "美食1"
						}, {
							img: '2',
							text: "美食2"
						},
						{
							img: '3',
							text: "美食3"
						}, {
							img: '4',
							text: "美食4"
						},
						{
							img: '5',
							text: "美食5"
						}, {
							img: '6',
							text: "美食6"
						}
					],
					[{
						img: 'a',
						text: "a"
					}, {
						img: 'b',
						text: "b"
					}],
				]
			}
		},
		methods:{
			bannerfun(e){
				this.num=e.detail.current
			}
		}
	}
</script>

<style scoped>
	.search-view image {
		width: 35upx;
		height: 35upx;
	}

	.search-view {
		font-size: 38upx;
		font-weight: bold;
		display: flex;
		align-items: center;
		height: 80upx;
	}

	.search-text {
		padding: 0 10upx;
	}

	/*搜索*/
	.search-img {
		margin: auto 0 auto 20upx;
		width: 40upx;
		height: 40upx;
	}

	.search {
		height: 70upx;
		line-height: 70upx;
		width: 100%;
		display: flex;
		flex-direction: flex;
		background: #eff3f4;
		border-radius: 10rpx;
	}

	.search input {
		height: 70upx;
		line-height: 70upx;
		width: 100%;
		font-size: 25upx;
		color: #666666;
	}

	.search-cont {
		display: flex;
		justify-content: space-between;
		height: 70upx;
		align-items: center;
	}

	swiper {
		height: 320upx !important;
	}

	.swiper-item {
		display: fLex;
		flex-wrop: wrap;
		align-itens: center;
		justify-content: space-between;
		height: 320upx;
	}

	.conteng-img {
		width: calc((100% / 5) . 12px) !important;
		margin: 6px;
		/* height: 128upx; */
		position: relative;
		text-align: center;
	}

	.conteng-img text {
		podding-top: 20upx;
		font-size: 25upx;
	}

	.uploadimg {
		width: 70upx;
		height: 7eupx;
		border-rodius: 5eupx;
		display: block;
		margin: 0 auto;
	}

	/*指示点*/
	.instruct-view {
		display: flex;
		justify-content: center;
		padding-top: 10upx;
	}

	.instruct {
		background: #e6e606;
		height: 10upx;
		width: 30upx;
		border-radius: 50upx;
		margin: 0 10upx;
	}

	.active {
		background: #fbae22 !important;
	}
</style>
