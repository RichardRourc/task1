<template>
	<view class="shop-detail">
		<shop-detail />
	</view>
</template>

<script>
	import shopDetail from './components/shop-contact';
	
	export default {
		data() {
			return {
				
			}
		},
		components: {
			'shop-detail': shopDetail,
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.shop-detail{
		padding: 32upx;
	}
</style>
