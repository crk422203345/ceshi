<template>
	<view>
		<view class="box">
			<view class="title">
				<view class="left">
					<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/a429cf00-4a4e-11eb-bd01-97bc1429a9ff.png"
					 mode="" style="width: 20px;height: 20px;background-color: rgb(58,218,162);border-radius: 50%;vertical-align: middle;"></image>
					<text style="font-weight:bold;margin-left:5px">临时任务:洗扫</text>
				</view>
				<view class="right">
					<text style="color:red">{{obj.taskStatus}}</text>
				</view>
			</view>
			<view class="line"></view>
			<view class="body">
				<view class="list-item"><text>任务名称：</text>{{obj.taskName}}</view>
				<view class="list-item"><text>任务类型：</text>{{obj.taskType}}</view>
				<view class="list-item"><text>任务状态：</text>{{obj.taskStatus}}</view>
				<view class="list-item"><text>排班时间：</text>{{obj.startDate}}到{{obj.endDate}}</view>
				<view class="list-item"><text>作业内容：</text>{{obj.taskContent}}</view>
				<view class="list-item"><text>创建时间：</text>{{obj.modifyTime}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				obj: {},
				name: '洗扫'
			}
		},
		onLoad(e) {
			var that = this;
			uni.request({
				url: 'http://139.9.169.87:9002/app/Task/getTaskById?id=' + e.id,
				method: 'GET',
				success(res) {
					console.log(res)
					uni.showToast({
						title: '数据加载成功',
						icon: 'success'
					})
					that.obj = res.data.data
				}
			})
		},
		beforeCreate() {
			uni.showToast({
				title: '数据加载中',
				icon: 'loading',
			})
		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	.box {
		width: 84%;
		padding: 10px 3%;
		min-height: 200px;
		margin: 20px auto 0;
		box-shadow: 0 0 2px #e1e1e1;

		.title {
			display: flex;
			flex-direction: row;

			.left {
				flex: 1;
				display: flex;
				justify-content: flex-start;
			}

			.right {
				flex: 1;
				display: flex;
				justify-content: flex-end;
			}
		}

		.line {
			width: 100%;
			margin: 10px auto;
			height: 1rpx;
			background: #ececec;
		}

		.body {
			width: 100%;
			padding: 0 5px;

			.list-item {
				margin: 10px auto;
				font-size: 13px;
			}

			text {
				color: #acacac;
			}
		}
	}
</style>
