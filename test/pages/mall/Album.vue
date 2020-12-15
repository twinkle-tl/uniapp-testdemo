<template>
	<view>
		<view class="album-container">
			<view class="left">
				<image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/d692a30ee3d586c4274575eec255d3c5.jpg?thumb=1&w=358&h=508"
				 mode=""></image>
			</view>
			<view class="right flex-col">
				<image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/4aea81c738383c9787b49c3d5e6a7ab0.jpg?thumb=1&w=358&h=252"
				 mode=""></image>
				<image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/267e988a99b5cf4e960747e8aa5fa831.jpg?thumb=1&w=358&h=252"
				 mode=""></image>
			</view>
		</view>
		<view class="recommend-container">
			<image src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/89e6857b593e44d600f26544c602fd73.jpg?thumb=1&w=720&h=280"
			 mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		name: "HomeAlbum",
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	.album-container {
		display: flex;
		background-color: #fff;
		margin-bottom: 16rpx;
	}

	.left {
		flex: 1;
		box-sizing: border-box;
		height: 530rpx;
		padding-right: 6rpx;
	}

	.left image {
		width: 100%;
		height: 100%;
	}

	.right {
		width: 373rpx;
	}

	.right image {
		width: 100%;
		height: calc(50% - 2rpx)
	}

	.recommend-container {
		margin-bottom: 16rpx;
	}

	.recommend-container image {
		width: 100%;
		height: 292rpx;
	}
</style>
