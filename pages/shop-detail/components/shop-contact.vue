<template>
	<div class="shop-contact">
		<div class="shop-contact__name">
			{{ obj.shopName }}
		</div>
		<div class="shop-contact__info">
			<div class="shop-contact__info--detail">
				<div class="time item">
					 <span class="detail">营业时间</span>   {{ obj.timeStart }}:00 - {{ obj.timeEnd }}:00
				</div>
				<div class="address item">
					<span class="detail">门店地址</span>   {{ obj.shopAddress }}
				</div>
			</div>
			<div class="call" @click="callNumber"></div>
		</div>
		<div class="map"></div>
		<div class="order-now">
			马上下单
		</div>
	</div>
</template>

<script>
	const obj = {
		shopName: '碳烤吧',
		timeStart: 9,
		timeEnd: 21,
		shopAddress: '天河区中山大道87号商品码头美食广场'
	};
	
	export default {
		data () {
			return {
				obj
			}
		},
		methods: {
			callNumber () {
				uni.makePhoneCall ({
					 phoneNumber: '123',
					 success () {
						 console.log(yes)
					 },
					 fail () {
						 console.log(no)
					 }
				})
			}
		}
	}
</script>

<style lang="scss">
	.shop-contact__name{
		padding-bottom: 24upx;
		font-weight: bold;
		font-size: 32upx;
	}
	.shop-contact__info{
		display: flex;
		justify-content: space-between;
	}
	.shop-contact__info--detail{
		font-size: 20upx;
		color: #404040;
	}
	.item{
		margin-bottom: 12upx;

	}
	.detail{
		margin-right: 16upx;
		font-size: 24upx;
		color: #999999;
	}
	.call{
		width: 60upx;
		height: 60upx;
		background-color: #F8D6BB;
		border-radius: 12upx;
	}
	.map{
		width: 686upx;
		height: 200upx;
		margin-top: 36upx;
		background-color: #aaa;
	}
	.order-now{
		position: fixed;
		bottom: 48upx;
		width: 694upx;
		height: 80upx;
		border-radius: 160upx;
		text-align: center;
		line-height: 80upx;
		font-size: 32upx;
		color: #404040;
		background-color: $button-color;
	}
</style>
