<template>
	<view class="card" :class="getCardClass">
		<view v-if="showhead" class="p-2 d-flex j-sb a-center" :class="getHeadClass" :style="headStyle">
			<text class="font-md text-dark" :class="getTitleClass" :style="headTitleStyle">{{title}}</text>
			<view class="font d-flex j-sb a-center text-muted" v-if="showheadRight">
				{{headRightText}}
				<view  v-if="showheadRight&&showheadRightIcon" class="iconfont iconyou text-muted ml" style="font-size: 25upx;">
				</view>
				<slot name="right" />
			</view>
		</view>
		<view :class="getBodyClass" :style="bodyStyle" class="card-body">
			<image v-if="cover" :src="cover" :style="getCoverStyle" class="w-100" mode="widthFix"></image>
			<slot />
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			showhead:{
				type: Boolean,
				default: true
			},
			title: String,
			titleWeight:{
				type: Boolean,
				default: true
			},
			showheadRight:{
				type: Boolean,
				default: false
			},
			headRightText: String,
			headBorderTop:{
				type: Boolean,
				default: false
			},
			headBorderBottom:{
				type: Boolean,
				default: false
			},
			showheadRightIcon:{
				type: Boolean,
				default: false
			},
			cover: String,
			bodyPadding:{
				type: Boolean,
				default: false
			},
			headStyle: String,
			headTitleStyle: String,
			titleFontSize:{
				type: String,
				default: 'md'
			},
			bodyStyle: String,
			cardBorder:{
				type: Boolean,
				default: false
			},
			cardRounded:{
				type: Boolean,
				default: false
			},
			cardShadow:{
				type: Boolean,
				default: false
			},
			coverHeight: String,
		},
		methods:{
			linkPage(obj){
				
			}
		},
		computed:{
			getCardClass(){
				let border = this.cardBorder?'border border-light-secondary':''
				let rounded = this.cardRounded?'rounded':''
				let shadow = this.cardShadow?'shadow':''
				return `${border} ${rounded} ${shadow}`
			},
			getHeadClass(){
				let borderBottom = this.headBorderBottom?'border-bottom border-light-secondary':''
				let borderTop = this.borderTop?'border-top border-light-secondary':''
				return `${borderBottom} ${borderTop}`
			},
			getTitleClass(){
				let fontWeight = this.titleWeight?'font-weight':''
				let fontSize = 'font'+this.titleFontSize
				return `${fontWeight} ${fontSize}`
			},
			getBodyClass(){
				return this.bodyPadding?'p-2':''
			},
			getCoverStyle(){
				if(this.coverHeight){
					let height =uni.upx2px(parseInt(this.coverHeight))
					return `height:${height}px`
				}
			}
		}
	}
</script>

<style scoped>
	.rounded{border-radius: 12upx !important;}
	.card .card-body{overflow: hidden;}
</style>
