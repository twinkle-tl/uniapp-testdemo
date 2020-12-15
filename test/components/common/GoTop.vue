<template>
    <view v-show="show">
        <view class="fixed-br">
            <image class="money" src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/a5bd951d960c0ad6ea2c54770edfb2ff.gif" mode=""></image>
            <image @click="goTop" class="go-top" src="https://m.mi.com/static/img/top.451d650ecd.png" mode=""></image>
        </view>
    </view>
</template>

<script>
export default {
    name: 'goTop',
    props:{
        show:{
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            
        }
    },
    methods: {
        goTop(){
            uni.pageScrollTo({
                scrollTop: 0,
                duration: 100
            });
        }
    },
}
</script>

<style scoped>
    .fixed-br {
      position: fixed;
      bottom: calc(var(--window-bottom) + 40rpx);
      right: 26rpx;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .fixed-br .money {
      width: 116rpx;
      height: 116rpx;
      margin-bottom: 16rpx;
    }
    .fixed-br .go-top {
      width: 73rpx;
      height: 73rpx;
    }

</style>

