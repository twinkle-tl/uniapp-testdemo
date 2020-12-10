<template>
	<view class="content">
		<scroll-view scroll-x class="border-bottom scroll-row" style="height: 80upx;" >
			<view class="scroll-row-item px-3" 
			style="height: 80upx;line-height: 80upx;" 
			v-for="(item,index) in tabBars" :key="index" 
			:class="tabIndex ==index?'main-text-color':''">
				<text class="font-md">{{item.name}}</text>
			</view>
		</scroll-view>
		<swiper :duration="150" :current="tabIndex" :style="'height:'+scrollH +'px;'" @change="onChangeTab">
			<swiper-item v-for="(item,index) in newsitems" :key="index">
				<scroll-view scroll-y class="border-bottom scroll-row" :style="'height:'+scrollH +'px;'" @scrolltolower="loadmore(index)">
					<block v-for="(list, listIndex) in item.list" :key="listIndex">
						<swiper-image v-if="list.type == 'swiper'" :resdata="list.data" />
						
						<template v-else-if="list.type == 'indexnavs'">
							<index-nav :resdata="list.data" />
							<divider />
						</template>
						
						<template v-else-if="list.type == 'threeAdv'">
							<three-adv :resdata="list.data" />
							<divider />
						</template>
						
						<!-- <card headTitle="每日精选" bodyCover="http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png" /> -->
						
						<view class="row j-sb" v-else-if="list.type == 'list'">
							<block v-for="(item2, index2) in list.data" :key="index2">
								<common-list :item="item2" :index="index2" />
							</block>
						</view>
					</block>
					
					<divider></divider>
					<view class="d-flex a-center j-center text-light-muted font-md py-3">
						{{item.loadtext}}
					</view>
				</scroll-view>
			</swiper-item>
		</swiper>
		
		<!-- 
		
		<view class="card">
			<view class="font-md font-weight p-1 border-bottom main-border-color">
				标题
			</view>
			<view class="">
				1
			</view>
		</view> -->
	</view>
</template>

<script>
	// 模拟后端数据
	let demoTabBars=[
		{
			name: '关注'
		},
		{
			name: '推荐'
		},
		{
			name: '体育'
		},
		{
			name: '热点'
		},
		{
			name: '财经'
		},
		{
			name: '体育'
		},{
			name: '关注'
		},
		{
			name: '推荐'
		},
		{
			name: '体育'
		}
	]
	
	let demo1=[
		{
			type: "swiper",
			data:[
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png'
				},
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-14055815229.png'
				}
			]
		},
		{
			type: "indexnavs",
			data:[
				{
					src: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2094165846,1414094421&fm=26&gp=0.jpg',
					text: "新品发布"
				},
				{
					src: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2094165846,1414094421&fm=26&gp=0.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2094165846,1414094421&fm=26&gp=0.jpg',
					text: "新品发布"
				},
				{
					src: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2094165846,1414094421&fm=26&gp=0.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2094165846,1414094421&fm=26&gp=0.jpg',
					text: "小米众筹"
				}
			]
		},
		{
			type: "threeAdv",
			data:{
				big:{
					src:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3171647731,1116863158&fm=26&gp=0.jpg'
				},
				smalltop:{
					src:'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3848402655,92542552&fm=26&gp=0.jpg'
				},
				smallbottom:{
					src:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg'
				},
			},
		},
		{
			type: "list",
			data:[
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				}
			]
		},
	]
		
	let demo2=[
		{
			type: "swiper",
			data:[
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png'
				},
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-14055815229.png'
				}
			]
		},
		{
			type: "indexnavs",
			data:[
				{
					src: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png',
					text: "新品发布"
				},
				{
					src: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-14055815229.png',
					text: "小米众筹"
				},
				{
					src: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png',
					text: "新品发布"
				},
				{
					src: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-14055815229.png',
					text: "小米众筹"
				},
				{
					src: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-14055815229.png',
					text: "小米众筹"
				}
			]
		},
		{
			type: "threeAdv",
			data:{
				big:{
					src:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3171647731,1116863158&fm=26&gp=0.jpg'
				},
				smalltop:{
					src:'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3848402655,92542552&fm=26&gp=0.jpg'
				},
				smallbottom:{
					src:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg'
				},
			},
		},
		{
			type: "list",
			data:[
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				},
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调',
					desc:'1.5匹变频',
					oprice:2699,
					pprice:1399,
				}
			]
		},
	]
	
	import swiperImage from '@/components/index/swiper-image.vue'
	import indexNav from '@/components/index/index-nav.vue'
	import threeAdv from '@/components/index/three-adv.vue'
	import card from '@/components/index/card.vue'
	import commonList from '@/components/index/common-list.vue'
	export default {
		components:{
			swiperImage,
			indexNav,
			threeAdv,
			card,
			commonList,
		},
		data() {
			return {
				scrollinto: "",
				scrollH: 500,
				tabIndex: 0,
				tabBars: [],
				newsitems: [],
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					this.scrollH = res.windowHeight - uni.upx2px(80+2)
				}
			})
			this.__init()
		},
		methods: {
			__init(){
				this.tabBars = demoTabBars
				let arr=[]
				for(var i=0; i<this.tabBars.length;i++){
					let obj={
						list:[],
						//1. 上拉加载更多  2.加载中  3.没有更多了
						loadtext: "上拉加载更多"
					}
					// 获取首屏数据
					if(i===0){
						obj.list = demo1
					}
					arr.push(obj)	
				}
				this.newsitems = arr
			},
			//切换选项卡
			changeTab(index){
				if(this.tabIndex === index){
					return;
				}
				this.tabIndex = index
				this.scrollinto = 'tab'+index
				this.addData()
			},
			//监听滑动列表
			onChangeTab(e){
				this.changeTab(e.detail.current)
			},
			//加载数据
			addData(){
				let index=this.tabIndex
				this.newsitems[index].list = demo2
			},
			loadmore(index){
				let item=this.newsitems[index]
				if(item.loadtext !== '上拉加载更多'){
					return
				}
				item.loadtext = '加载中...'
				setTimeout(()=>{
					// 加载数据
					item.list =[...item.list, ...demo2]
					// 恢复状态
					item.loadtext = '上拉加载更多'
				},2000)
			}
		}
	}
</script>

<style scoped>
	.content{
		padding: 0;
	}
</style>
