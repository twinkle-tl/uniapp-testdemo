<template>
	<view class="my-container">
		<my-header></my-header>
        <option-list></option-list>
	</view>
</template>

<script>
import MyHeader from './Header'
import OptionList from './OptionList'

export default {
    components:{
        MyHeader,
        OptionList
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
    .my-container {
      height: 100vh;
      background: #f5f5f5;
    }
</style>
