<template>
	<view>
		<view class="title">
			账号密码登录
		</view>
		<view class="col">
			<uni-forms :value="formData" ref="form">
				<uni-forms-item name="name">
					<uni-easyinput type="text" v-model="formData.name" placeholder="请输入用户名/邮箱/用户名" :styles="styles"></uni-easyinput>
				</uni-forms-item>
				<uni-forms-item required name="pwd">
					<uni-easyinput type="password" v-model="formData.pwd" placeholder="请输入密码" :styles="styles"></uni-easyinput>
				</uni-forms-item>
				<button @click="submitForm">登录</button>
			</uni-forms>
			<view class="box">
				<view class="boxs">
					忘记密码
				</view>
				<view class="box1">
					新用户<text style="color: red;">注册</text>
				</view>
			</view>
		</view>
		<view class="foot-title">
			第三方登录
		</view>
		<view class="foot">
			<view class="foot-son">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/90c5e8e0-4a3a-11eb-b680-7980c8a877b8.png"
				 mode=""></image>
			</view>
			<view class="foot-son">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/900d4740-4a3a-11eb-97b7-0dc4655d6e68.png"
				 mode=""></image>
			</view>
			<view class="foot-son">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/8f320270-4a3a-11eb-97b7-0dc4655d6e68.png"
				 mode=""></image>
			</view>
		</view>
		<neil-modal :show="show1" title="提示" content="请输入用户名或密码" align="center" :show-cancel="false" @close="doClose1"
		 confirm-color="#3adaa2">
		</neil-modal>
		<neil-modal :show="show" title="提示" content="请输入正确用户名或密码" align="center" :show-cancel="false" @close="doClose"
		 confirm-color="#3adaa2">
		</neil-modal>
		<neil-modal :show="shows" title="提示" content="登陆成功" align="center" :show-cancel="false" @close="doCloses"
		 confirm-color="#3adaa2">
		</neil-modal>
	</view>
</template>

<script>
	import qs from 'qs';
	export default {
		data() {
			return {
				show1:false,
				show: false,
				shows: false,
				formData: {
					name: '',
					pwd: ''
				},
				styles: {
					borderColor: "transparent"
				}
			}
		},

		onLoad() {

		},
		methods: {
			submitForm(form) {
				// 手动提交表单
				if(this.formData.name==''||this.formData.pwd==''){
					this.show1=true;
				}else{
				this.login();	
				}
				
			},
			login() {
				var that = this;
				var datas = qs.stringify({
					loginName: this.formData.name,
					loginPassword: this.formData.pwd
				})
				uni.request({
					url: 'http://139.9.169.87:9002/app/Employee/doLogin',
					method: 'POST',
					data: datas,
					header: {
						'content-type': 'application/x-www-form-urlencoded',
					},
					success(res) {
						if (res.data.status == 200) {
							that.shows = true;
						} else if (res.data.status == 400) {
							that.show = true
						}
					},
					fail(res) {
						console.log(res)
					}
				})
			},
			doClose() {
				this.show = false
			},
			doClose1() {
				this.show1 = false
			},
			doCloses() {
				this.shows = false
				uni.switchTab({
					url: '/pages/home/home'
				})
			}

		}
	}
</script>

<style lang="scss" scoped>
	.title {
		font-size: 24px;
		font-family: '等线';
		font-weight: bold;
		padding: 34% 7% 6%;
	}

	/deep/.uni-easyinput {
		border-bottom: 1px solid rgba($color: #d4d4d4, $alpha: .4);
		margin: 0 auto;
	}

	button {
		background-color: rgb(58, 218, 162) !important;
		border-radius: 20px !important;
		border: none !important;
		width: 95% !important;
		color: white;
		font-size: 14px;
		padding: 5px 0;
	}

	.box {
		margin: 5px auto;
		width: 90%;
		display: flex;
		flex-direction: row;

		.boxs {
			flex: 1;
			display: flex;
			justify-content: flex-start;
			align-items: center;
			font-size: 14px;
		}

		.box1 {
			flex: 1;
			font-size: 14px;
			display: flex;
			justify-content: flex-end;
			align-items: center;
		}
	}

	.foot-title {
		position: fixed;
		left: 50%;
		transform: translateX(-50%);
		bottom: 80px;
		font-family: '等线';
		font-weight: bold;
		color: #cccccc;
	}

	.foot {
		width: 60%;
		display: flex;
		flex-direction: wrap;
		position: fixed;
		left: 50%;
		transform: translateX(-50%);
		bottom: 20px;

		image {
			width: 40px;
			height: 40px;
		}

		.foot-son {
			width: 30%;
			display: flex;
			justify-content: center;
		}
	}
</style>
