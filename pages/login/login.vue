<template>
	<view class="login">
		<div class="avatar" v-if="!avatarUrl"></div>
		<img  alt="" v-else :src="avatarUrl" class="avatar">
		
		
		<br>
		<span class="more">开启更多功能</span>
		<br>
		<!-- #ifdef MP-WEIXIN -->
		<button class="login__button" @getuserinfo="login" open-type="getUserInfo">登录</button>
		<!-- #endif -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				SessionKey: '',
                OpenId: '',
                nickName: null,
                avatarUrl: null,
                isCanUse: uni.getStorageSync('isCanUse')||true//默认为true
			}
		},
		methods: {
			wxGetUserInfo() {
                let _this = this;
                
            },
			//登录
			login() {
				let _this = this;
				uni.showLoading({
					title: '登录中...'
				});
				// 1.wx获取登录用户code
                uni.login({
                    provider: 'weixin',
                    success: function(loginRes) {
                        let code = loginRes.code;
                        if (!_this.isCanUse) {
                            //非第一次授权获取用户信息
                            uni.getUserInfo({
                                provider: 'weixin',
                                success: function(infoRes) {
 　　　　　　　　　　　　　　　　　　　　　　//获取用户信息后向调用信息更新方法
                                    let nickName = infoRes.userInfo.nickName; //昵称
                                    let avatarUrl = infoRes.userInfo.avatarUrl; //头像
									_this.nickName = nickName;
									_this.avatarUrl = avatarUrl;
									uni.hideLoading();

                                        // _this.updateUserInfo();//调用更新信息方法
                                }
                            });
                        }
            
                        //2.将用户登录code传递到后台置换用户SessionKey、OpenId等信息
                        // uni.request({
                        //     // url: '服务器地址',
                        //     // data: {
                        //     //     code: code,
                        //     // },
                        //     // method: 'GET',
                        //     // header: {
                        //     //     'content-type': 'application/json'
                        //     },
                        //     success: (res) => {
                        //         //openId、或SessionKdy存储//隐藏loading
                        //         uni.hideLoading();
                        //     }
                        // });
                    },
                });
				uni.getUserInfo({
				    provider: 'weixin',
				    success: function(infoRes) {
				        let nickName = infoRes.userInfo.nickName; //昵称
				        let avatarUrl = infoRes.userInfo.avatarUrl; //头像
						console.log(avatarUrl)
						_this.nickName = nickName;
						_this.avatarUrl = avatarUrl;
						
						_this.isCanUse = false;
						uni.hideLoading();

				        try {
				            uni.setStorageSync('isCanUse', false);//记录是否第一次授权  false:表示不是第一次授权
				            _this.updateUserInfo();
				        } catch (e) {}
				    },
				    fail(res) {
						console.log(res)
					}
				});
            },
         //向后台更新信息
            updateUserInfo() {
                // let _this = this;
                // uni.request({
                //     url:'url' ,//服务器端地址
                //     data: {
                //         appKey: this.$store.state.appKey,
                //         customerId: _this.customerId,
                //         nickName: _this.nickName,
                //         headUrl: _this.avatarUrl
                //     },
                //     method: 'POST',
                //     header: {
                //         'content-type': 'application/json'
                //     },
                //     success: (res) => {
                //         if (res.data.state == "success") {
                //             uni.reLaunch({//信息更新成功后跳转到小程序首页
                //                 url: '/pages/index/index'
                //             });
                //         }
                //     }
                //    
                // });
            // }
        },
			}
	}
</script>

<style lang="scss">
	.login{
		padding-top: 116upx;
		text-align: center;
	}
	.avatar{
		display: inline-block;
		width: 192upx;
		height: 194upx;
		background-color: #666;
		margin-bottom: 64upx;
		border-radius: 124upx;
	}
	.more{
		display: inline-block;
		// width: 144upx;
		// height: 34upx;
		margin-bottom: 180upx;
		font-size: 24upx;
		color: #999999;
		
	}
	.login__button{
		display: inline-block;
		width: 480upx;
		height: 80upx;
		border-radius: 160upx;
		background-color: $button-color;
		text-align: center;
		line-height: 80upx;
		color: #404040;
		font-size: 32upx;
		box-shadow:0px 0px 20px rgba(248,214,187,1)
	}
</style>
