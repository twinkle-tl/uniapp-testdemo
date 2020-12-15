<template>
	<view>
        <no-login></no-login>
        <recommend-list></recommend-list>
	</view>
</template>

<script>
import NoLogin from './NoLogin'
import RecommendList from './RecommendList'
export default {
    components:{
        RecommendList,
        NoLogin
    },
    data() {
        return {
            
        }
    },
    methods: {
        
    },
}
</script>

<style scoped>
    
</style>
