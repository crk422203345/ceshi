<template>
	<view class="app">
		<view class="info">
			<view class="img_toux">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/28b6b210-4982-11eb-97b7-0dc4655d6e68.png"
				 mode="" class="img"></image>
			</view>
			<view class="contents">
				<view class="name">
					{{info.name}}
				</view>
				<view class="phone">
					手机号：{{info.phone}}
				</view>
			</view>
			<view class="img_touxs">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dba0f370-4ab0-11eb-b997-9918a5dda011.png"
				 mode="" class="img"></image>
			</view>
		</view>
		<view class="line">

		</view>
		<view class="xg">
			<view class="xs">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dba0f370-4ab0-11eb-b997-9918a5dda011.png"
				 mode="" style="width:21px ;height: 21px"></image><text style="margin-left: 5px;">我的上报</text>
			</view>
			<view class="ximg">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/fe8a8580-49a3-11eb-a16f-5b3e54966275.png"
				 mode="" style="width:16px ;height: 16px;"></image>
			</view>
		</view>
		<view class="xg">
			<view class="xs">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dba0f370-4ab0-11eb-b997-9918a5dda011.png"
				 mode="" style="width:21px ;height: 21px"></image><text style="margin-left: 5px;">消息</text>
			</view>
			<view class="ximg">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/fe8a8580-49a3-11eb-a16f-5b3e54966275.png"
				 mode="" style="width:16px ;height: 16px;"></image>
			</view>
		</view>
		<view class="xg">
			<view class="xs">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dba0f370-4ab0-11eb-b997-9918a5dda011.png"
				 mode="" style="width:21px ;height: 21px"></image><text style="margin-left: 5px;">意见反馈</text>
			</view>
			<view class="ximg">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/fe8a8580-49a3-11eb-a16f-5b3e54966275.png"
				 mode="" style="width:16px ;height: 16px;"></image>
			</view>
		</view>
		<view class="xg">
			<view class="xs">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dba0f370-4ab0-11eb-b997-9918a5dda011.png"
				 mode="" style="width:21px ;height: 21px"></image><text style="margin-left: 5px;">设置</text>
			</view>
			<view class="ximg">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/fe8a8580-49a3-11eb-a16f-5b3e54966275.png"
				 mode="" style="width:16px ;height: 16px;"></image>
			</view>
		</view>
		<view class="xg">
			<view class="xs">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dba0f370-4ab0-11eb-b997-9918a5dda011.png"
				 mode="" style="width:21px ;height: 21px"></image><text style="margin-left: 5px;">关于我们</text>
			</view>
			<view class="ximg">
				<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/fe8a8580-49a3-11eb-a16f-5b3e54966275.png"
				 mode="" style="width:16px ;height: 16px;"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		
		data() {
			return {
				info: {
					name: 'admin',
					phone: 12345678910
				}
			}
		},

		methods: {
		
		}
	}
</script>

<style lang="scss" scoped>
	.app {
		padding-top: 1px;

		.info {
			display: flex;
			flex-wrap: wrap;
			width: 90%;
			height: 75px;
			padding: 10px 5%;
			margin: 10px auto;

			.img_toux {
				width: 30%;
				display: flex;
				align-items: center;

				.img {
					width: 75px;
					height: 75px;
					border-radius: 50%;
				}
			}

			.img_touxs {
				width: 10%;
				display: flex;
				align-items: center;
				justify-content: flex-end;
				.img {
					width: 20px;
					height: 20px;
					border-radius: 50%;
					
				}
			}

			.contents {
				width: 60%;
				display: flex;
				flex-wrap: wrap;

				.name {
					width: 100%;
					font-weight: bold;
					font-size: 20px;
					display: flex;
					align-items: center;
				}

				.phone {
					width: 100%;
					font-size: 13px;
					display: flex;
					align-items: center;
				}
			}
		}

		.line {
			height: 5px;
			width: 100%;
			background-color: #ebebeb;
		}

		.xg {
			height: 70px;
			border-bottom: 1px solid #f0f0f0;
			display: flex;
			width: 90%;
			align-items: center;
			margin: 0 auto;
			flex-direction: row;
			.xs {
				flex: 1;
				display: flex;
				justify-content: flex-start;
				text{
					font-family:'等线' ;
					display: inline-flex;
					align-items: center;
				}
			}

			.ximg {
				flex: 1;
				display: flex;
				justify-content: flex-end;
			}
		}
	}
</style>
