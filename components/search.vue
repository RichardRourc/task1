<template>
	<div class="search">
		<div class="search-icon"></div>
		<input type="text" class="search__item" placeholder="搜索门店" />
	</div>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	.search{
		display: flex;
		align-items: center;
		width: 688upx;
		height: 72upx;
		margin-bottom: 32upx;
		background-color: #F5F5F5;
		border-radius: 16upx;
		line-height: 72upx;
		font-size: 32upx;
		color: #CECECE;
		
	}
	.search-icon{
		display: inline-block;
		background-color: #999;
		width: 28upx;
		height: 28upx;
		margin-left: 32upx;
	}
	.search__item{
		display: inline-block;
		padding-left: 32upx;
	}
</style>
