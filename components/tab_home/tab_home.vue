<template>
	<view class="content">
		<aloys-tab :tabs="tabs" @change="onTabChange">
			<view slot="content0">
				<view class="list_box">
					<view class="list_item" v-for="(item,index) in arr" :key="index">
						<view class="left">
							<view class="left-top">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/a429cf00-4a4e-11eb-bd01-97bc1429a9ff.png"
								 mode="" style="width: 20px;height: 20px;background-color: rgb(58,218,162);border-radius: 50%;vertical-align: middle;"></image>
								<text>{{item.taskType}}:{{item.taskName}}</text>
							</view>
							<view class="left-bottom">
								任务状态:<text style="color: red;">{{item.taskStatus}}</text>
							</view>
						</view>
						<view class="right">
							<button @click="tz(item.id)">查看详情</button>
						</view>
					</view>
				</view>
			</view>
			<view slot="content1">
				<view class="list_box">
					<view class="list_item" v-for="(item,index) in arr" :key="index">
						<view class="left">
							<view class="left-top">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/a429cf00-4a4e-11eb-bd01-97bc1429a9ff.png"
								 mode="" style="width: 20px;height: 20px;background-color: rgb(58,218,162);border-radius: 50%;vertical-align: middle;"></image>
								<text>{{item.taskType}}:{{item.taskName}}</text>
							</view>
							<view class="left-bottom">
								任务状态:<text style="color: red;">{{item.taskStatus}}</text>
							</view>
						</view>
						<view class="right">
							<button @click="tz(item.id)">查看详情</button>
						</view>
					</view>
				</view>
			</view>
			<view slot="content2">
				<view class="list_box">
					<view class="list_item" v-for="(item,index) in arr" :key="index">
						<view class="left">
							<view class="left-top">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/a429cf00-4a4e-11eb-bd01-97bc1429a9ff.png"
								 mode="" style="width: 20px;height: 20px;background-color: rgb(58,218,162);border-radius: 50%;vertical-align: middle;"></image>
								<text>{{item.taskType}}:{{item.taskName}}</text>
							</view>
							<view class="left-bottom">
								任务状态:<text style="color: red;">{{item.taskStatus}}</text>
							</view>
						</view>
						<view class="right">
							<button @click="tz(item.id)">查看详情</button>
						</view>
					</view>
				</view>
			</view>
			<view slot="content3">
				<view class="list_box">
					<view class="list_item" v-for="(item,index) in arr" :key="index">
						<view class="left">
							<view class="left-top">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/a429cf00-4a4e-11eb-bd01-97bc1429a9ff.png"
								 mode="" style="width: 20px;height: 20px;background-color: rgb(58,218,162);border-radius: 50%;vertical-align: middle;"></image>
								<text>{{item.taskType}}:{{item.taskName}}</text>
							</view>
							<view class="left-bottom">
								任务状态:<text style="color: red;">{{item.taskStatus}}</text>
							</view>
						</view>
						<view class="right">
							<button @click="tz(item.id)">查看详情</button>
						</view>
					</view>
				</view>
			</view>
		</aloys-tab>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				tabs: [{
					title: '全部'
				}, {
					title: '未完成'
				}, {
					title: '进行中'
				}, {
					title: '已完成'
				}],
				arr: {},
				ww: '未完成'
			}
		},
		onLoad() {
			var that = this;
			uni.request({
				url: 'http://139.9.169.87:9002/app/Task/getTaskListAll',
				method: 'GET',
				success(res) {
					uni.showToast({
						title: '数据加载成功',
						icon: 'success'
					})
					that.arr = res.data.data
				}
			})
		},
beforeCreate(){uni.showToast({
				title: '数据加载中',
				icon: 'loading',
				duration:3000
			})},
		methods: {
			onTabChange(index) {

			},
			tz(id) {
				uni.navigateTo({
					url: "/components/tab_home_more/tab_home_more?id=" + id
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		position: absolute;
		height: 100%;
	}

	.list_box {
		width: 90%;
		margin: 10px auto;

		.list_item {
			width: 90%;
			margin: 10px 0;
			padding: 5px 5%;
			height: 60px;
			background-color: rgb(246, 247, 249);
			display: flex;
			flex-direction: row;
			border-radius: 10px;

			.left {
				flex: 1;
				display: flex;
				justify-content: center;
				flex-direction: column;

				.left-top {
					font-size: 18px;
					font-weight: bold;

					text {
						margin-left: 5px;
					}
				}

				.left-bottom {
					margin-top: 5px;
					font-size: 14px;
				}
			}

			.right {
				flex: 1;
				display: flex;
				justify-content: flex-end;
				align-items: center;

				button {
					margin: 0;
					padding: 0;
					border-radius: 20px;
					background: linear-gradient(to right, rgb(58, 218, 162), rgb(108, 215, 225));
					width: 90px;
					height: 35px;
					line-height: 35px;
					font-size: 13px;
					font-weight: bold;
					color: white;
					font-family: '等线';
				}
			}
		}
	}
</style>
