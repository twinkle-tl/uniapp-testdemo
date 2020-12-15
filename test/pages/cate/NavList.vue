<template>
    <view>
        <view class="list">
        	<view class="item" 
                v-for="(item,index) of list" 
                :class="{active:index==curretnNav}"
                @click="handleClickNav(index)"
                :key="index">新品{{index}}</view>
        </view>
    </view>
</template>

<script>
export default {
    name:'NavList',
    data() {
        return {
            list:['新品',2,3,4,5,6,7,8,9,10,11,12,13,14,15,16],
            curretnNav: 0
        }
    },
    watch:{
        curretnNav(val){
            this.$emit('navChange',val)
        },
       
    },
    methods: {
        handleClickNav(nav){
            this.curretnNav = nav
        },
        getName(){
            console.log('navvvvv');
        }
    }
}
</script>

<style scoped>
    .list {
      position: fixed;
      top: 0;
      bottom: var(--window-bottom);
      left: 0;
      width: 160rpx;
      box-sizing: border-box;
      border-right: 2rpx solid #efefef;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .list::-webkit-scrollbar {
      width: 0;
      height: 0;
      background: transparent;
    }
    .list .item {
      width: 100%;
      padding: 25rpx 0;
      text-align: center;
      transition: transform 0.1s linear;
    }
    .list .item.active {
      color: #fb7d34;
      transform-origin: center center;
      transform: scale(1.32);
    }

</style>
