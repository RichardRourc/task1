<template>
	<div class="nearby-shop">
		
		<search />
		<shop-list />
	</div>
</template>

<script>
	import search from '../../components/search'
	import shopList from './components/shop-list'
	
	export default {
		data() {
			return {
				
			};
		},
		methods: {},
		components: {
			search,
			'shop-list': shopList,
		},
	}
</script>

<style lang="scss">
	page{
		height: 100%;
	}
	.nearby-shop{
		padding: 32upx;
		display: flex;
		flex-direction: column;
		height: calc(100% - 64upx);
	}
	shop-list{
		height: calc(100% - 104upx);

	}
</style>
