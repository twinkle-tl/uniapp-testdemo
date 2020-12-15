<template>
	<view class="content">
		<block v-for="(list, listIndex) in dataList" :key="listIndex">
			<swiper-image v-if="list.type == 'swiper'" :resdata="list.data" />
			
			<template v-else-if="list.type == 'indexnavs'">
				<index-nav :resdata="list.data" />
				<divider />
			</template>
			
			<template v-else-if="list.type == 'threeAdv'">
				<three-adv :resdata="list.data" />
				<divider />
			</template>
			
			<card v-else-if="list.type == 'recommendAdv'" :title="list.data.title" :cover="list.data.cover" />
			
			<view class="row j-sb p-1 bg-light-secondary waterfall" v-else-if="list.type == 'list'">
				<block v-for="(item2, index2) in list.data" :key="index2">
					<common-list :resdata="item2" :index="index2" />
				</block>
			</view>
		</block>
		
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
	let demo1=[
		{
			type: "swiper",
			data:[
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png'
				},
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-14055815229.png'
				},
				{
					picture: 'http://hecaiwang.oss-cn-chengdu.aliyuncs.com/Images/20200628/2020628-1139431571413.png'
				},
			]
		},
		{
			type: "indexnavs",
			data:[
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443672&di=e2fd592d6337fd0b90d4897f4142327a&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F59570bfcb7dc699.jpg',
					text: "特卖",
				},
				{
					src: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607770443681&di=df2faf0201794d53ef66d86e7f938251&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_origin_min_pic%2F01%2F19%2F92%2F90570bffbae369f.jpg',
					text: "商城"
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
			type: "threeAdv",
			data:{
				big:{
					src:'https://s5.mogucdn.com/mlcdn/776a41/201203_3i93e886lehi861f21iac7f7b15g0_750x1125.png_640x854.v1cAC.40.webp'
				},
				smalltop:{
					src:'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2797163702,800261908&fm=26&gp=0.jpg'
				},
				smallbottom:{
					src:'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=2818096714,1358874082&fm=26&gp=0.jpg'
				},
			},
		},
		{
			type: "recommendAdv",
			data:{
				title:'每日精选',
				cover: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3908372508,454356706&fm=26&gp=0.jpg'
			},
		},
		{
			type: "list",
			data:[
				{
					cover:'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3621987426,796514073&fm=26&gp=0.jpg',
					title:'米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调米家空调',
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
				dataList: [],
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
				this.dataList = demo1
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
	.waterfall{column-count: 2;column-gap: 0;}
</style>
