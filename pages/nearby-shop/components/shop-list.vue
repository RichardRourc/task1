<template>
	
		
		<scroll-view scroll-y="true" class="shop-list"  @scrolltolower="addData" >
			<div class="shop-item" v-for=" item in arr " :key="item.id">
				<div class="shop-info">
					<div class="shop-info__name" :class="{ 'shop-info__name--relax': item.relax }">{{ item.name }}</div>
					<div class="shop-info__time" v-if="item.startTime">{{ item.startTime }}:00 - {{ item.endTime }}:00</div>
					<div class="shop-info__address" :class="{ 'shop-info__address--relax': item.relax }">{{ item.address }}</div>
				</div>
				<div class="relax shop-detail" v-if="item.relax">休息中</div>
				<div class="shop-detail" v-else>
					<div class="distance">{{ item.distance }}km</div>
					<div class="detail" v-if="item.startTime"></div>
					<div class="detail">门店详情 ></div>
				</div>
			</div>
			<!-- <div class="more">
				没有更多的门店了
			</div> -->
		</scroll-view>
	
	
</template>

<script>
	let arr = function () {
		let arr = [];
		
		for (var i = 0; i < 10; i++) {
			const obj = {
				id: i,
				name: '银河大厦',
				address: '天河区中山大道87号尚品码头美食广场',
				relax: false,
				distance: 32.26,
				startTime: 9,
				endTime: 21
			}
			arr[i] = obj;
		}
		
		
		arr[4].relax = true;
		arr[4].address = "啊 啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊aaaaaaaaaaaaaaaaaaaaaaaaaa";
		return arr;
	}()
	
	export default {
		data () {
			return {
				arr
			}
		},
		methods: {
			 addData: function () {
				 new Promise ( ( res, rej ) => {
					 uni.showLoading({
						title: '加载中'
					});
					 setTimeout ( () => {
						for ( let i = 0;i<10;i++ ){
							const obj = {
								id: i,
								name: '银河大厦',
								address: '天河区中山大道87号尚品码头美食广场',
								relax: false,
								distance: 32.26,
								startTime: 9,
								endTime: 21
							}
							uni.hideLoading();
							this.arr.push(obj);
						}
					}, 500 )
					res(this.arr)
					console.log(this.arr)
				} )
			},
		},
	}
</script>

<style lang="scss">
	.shop-list{
		height: calc(100%);
	}
	.shop-list::-webkit-scrollbar{
		display: none;
	}
	.shop-item{
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 20upx;
		margin-bottom: 28upx;
		border-bottom: 1upx solid #F9F9F9;
	}
	.shop-info{
		display: flex;
		flex-direction: column;
		align-content: space-between;
		color: #999;
		margin-right: 16upx;
	}
	.shop-info__name{
		font-size:28upx;
		font-weight: bold;
		padding: 8upx 0upx;
		color: #404040;
	}
	.shop-info__name--relax{
		opacity: .4;
	}
	.shop-info__address{
		// font-size: 28upx;
		width: 428upx;
		@include overFlow;
		padding: 8upx 0upx;

	}
	.shop-info__address--relax{
		opacity: .4;
	}
	.shop-detail{
		// display: inline-block;
		// flex-grow: 2;
		display: flex;
		flex-direction: column;
		height: 100%;
		align-content: space-between;
		color: #DFBEA9;
		text-align:right;

	}
	.distance{
		padding: 12upx 0upx;
		color: #404040;
	}
	.detail{
		padding: 12upx 0upx;
	}
	.relax{
		// height: 300upx;
		// text-align: center;
	}
	.more{
		color: #C7C7C7;
		font-size: $uni-font-size-base;
		text-align: center;
	}
</style>
