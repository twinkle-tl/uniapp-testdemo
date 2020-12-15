<template>
	<view>
		<nav-list @navChange="handleNavChange"></nav-list>
		<content-list :currentNav="currentNav" ></content-list>
		
		<!-- <view class="d-flex bg-white border-top position-fixed bottom-0 right-0 left-0" style="height: 90upx;">
			<view class="flex-1 d-flex j-center a-center flex-column line-h">
				<view class="iconfont iconxihuan line-h"></view>
				收藏
			</view>
			<view class="flex-1 d-flex j-center a-center flex-column line-h">
				<view class="iconfont icongouwuche line-h"></view>
				购物车
			</view>
			<view style="flex: 2.5;" class="text-white main-bg-color d-flex j-center a-center">
				加入购物车
			</view>
		</view> -->
	</view>
</template>

<script>
import NavList from'./NavList'
import ContentList from './ConList'
export default {
    components:{
        NavList,
        ContentList
    },
    data() {
        return {
            currentNav:'',
        }
    },
    methods: {
        handleNavChange(val){
            this.currentNav = val+'';
        }
    },
}
</script>

<style>

</style>
