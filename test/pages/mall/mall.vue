<template>
	<view class="home-container">
		<home-header @navChange="handleNavChange"></home-header>
        <home-banner></home-banner>
        <home-icons></home-icons>
        <home-album></home-album>
        <HomeMain></HomeMain>
        <go-top :show="showGoTop"></go-top>
        <!-- <view class="box"></view> -->
	</view>
</template>

<script>
import HomeHeader from './Header'
import HomeBanner from './Banner'
import HomeIcons from './Icons'
import HomeAlbum from './Album'
import HomeMain from './Main'
import GoTop from '../../components/common/GoTop.vue'
export default {
    components:{
        HomeHeader,
        HomeBanner,
        HomeIcons,
        HomeAlbum,
        HomeMain,
        GoTop
    },
    data() {
        return {
            showGoTop:false
        }
    },
    methods: {
        handleNavChange(val){
            console.log(val);
        }
    },
    onPageScroll(e){
        // console.log(e);
        if(e.scrollTop >= 773){
            this.showGoTop = true
        }else{
            this.showGoTop = false
        }
    },
}
</script>

<style scoped>
    .box{height: 600rpx}
        
    .home-container{
		background-color: #f5f5f5
	} 
</style>
