<template>
	<view class="content">
		<div @click="a">1</div>
		<div @click="b">2</div>
		<div @click="c">3</div>
		<scroll-view scroll-y></scroll-view>
	</view>
</template>

<script>
	
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		components: {
			
		},
		methods: {
			a () {
				uni.navigateTo({
					url: '../nearby-shop/nearby-shop'
				})	
			},
			b () {
				uni.navigateTo({
					url: '../shop-detail/shop-detail'
				})	
			},
			c () {
				uni.navigateTo({
					url: '../login/login'
				})	
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		paddgind: 8upx;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
