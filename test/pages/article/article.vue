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
						<template v-if="list.type == 'indexnavs'">
							<index-nav :resdata="list.data" />
							<divider />
						</template>
						<view class="row j-sb" v-else-if="list.type == 'list'">
							<block v-for="(item2, index2) in list.data" :key="index2">
								<common-list :resdata="item2" :index="index2" />
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
		
	</view>
</template>

<script>
	// 模拟后端数据
	let demoTabBars=[
		{
			name: '推荐'
		},
		{
			name: '美妆'
		},
		{
			name: '女装'
		},
		{
			name: '食品'
		},
		{
			name: '电脑'
		},
		{
			name: '百货'
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
			type: "indexnavs",
			data:[
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443672&di=e2fd592d6337fd0b90d4897f4142327a&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F59570bfcb7dc699.jpg',
					text: "资讯",
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443681&di=df2faf0201794d53ef66d86e7f938251&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F90570bffbae369f.jpg',
					text: "医院"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443667&di=e87c17ff132059345a4b90d6311cbc67&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_pic%2F01%2F19%2F74%2F00570b80ebe5640.jpg',
					text: "新品发布"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551005&di=3b46a87d723ccb135789e9016e189655&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F91%2F81570bf4830338d.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551005&di=28f549dda053fb683aa77fddae6c7e73&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F71570bfdc7d0b67.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551004&di=e3dd06aa146960206ecbb7af905cc226&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F93%2F52570c054b74eaa.jpg',
					text: "资讯"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770799598&di=eaf659dc827bd68dcb931d1b60fc9d16&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F98%2F68570c3a9a3a3d4.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551000&di=e270ea724e4bec2a7d69ffabf98b0f49&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F48%2F39570b25ee4e848.jpg',
					text: "新品发布"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770550999&di=2221db7d8a790dd452467ed9f0acbd00&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F87%2F43570bcb2645e00.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770770459&di=b66dbeb5018bf9d878565f505fa68a7f&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F52%2F29570b3549ece4d.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443681&di=df2faf0201794d53ef66d86e7f938251&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F90570bffbae369f.jpg',
					text: "医院"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443667&di=e87c17ff132059345a4b90d6311cbc67&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_pic%2F01%2F19%2F74%2F00570b80ebe5640.jpg',
					text: "新品发布"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551005&di=3b46a87d723ccb135789e9016e189655&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F91%2F81570bf4830338d.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551005&di=28f549dda053fb683aa77fddae6c7e73&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F71570bfdc7d0b67.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551004&di=e3dd06aa146960206ecbb7af905cc226&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F93%2F52570c054b74eaa.jpg',
					text: "资讯"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443672&di=e2fd592d6337fd0b90d4897f4142327a&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F59570bfcb7dc699.jpg',
					text: "资讯",
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443681&di=df2faf0201794d53ef66d86e7f938251&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F90570bffbae369f.jpg',
					text: "医院"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443667&di=e87c17ff132059345a4b90d6311cbc67&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_pic%2F01%2F19%2F74%2F00570b80ebe5640.jpg',
					text: "新品发布"
				},
			]
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
			type: "indexnavs",
			data:[
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443672&di=e2fd592d6337fd0b90d4897f4142327a&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F59570bfcb7dc699.jpg',
					text: "资讯",
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443681&di=df2faf0201794d53ef66d86e7f938251&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F90570bffbae369f.jpg',
					text: "医院"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443667&di=e87c17ff132059345a4b90d6311cbc67&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_pic%2F01%2F19%2F74%2F00570b80ebe5640.jpg',
					text: "新品发布"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551005&di=3b46a87d723ccb135789e9016e189655&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F91%2F81570bf4830338d.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551005&di=28f549dda053fb683aa77fddae6c7e73&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F71570bfdc7d0b67.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551004&di=e3dd06aa146960206ecbb7af905cc226&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F93%2F52570c054b74eaa.jpg',
					text: "资讯"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770799598&di=eaf659dc827bd68dcb931d1b60fc9d16&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F98%2F68570c3a9a3a3d4.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770551000&di=e270ea724e4bec2a7d69ffabf98b0f49&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F48%2F39570b25ee4e848.jpg',
					text: "新品发布"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770550999&di=2221db7d8a790dd452467ed9f0acbd00&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F87%2F43570bcb2645e00.jpg',
					text: "小米众筹"
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770770459&di=b66dbeb5018bf9d878565f505fa68a7f&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F52%2F29570b3549ece4d.jpg',
					text: "小米众筹"
				}
			]
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
	import indexNav from '@/components/index/index-scroll-nav.vue'
	import threeAdv from '@/components/index/three-adv.vue'
	import card from '@/components/common/card.vue'
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
