<template>
	<view>
		<view class="top">
			<view class="title">
				{{title}}
			</view>
			<view class="box_top">
				<view class="tops">
					<view class="tops_num">
						{{taskPesCount}}
					</view>
					<view class="tops_rw">
						今日作业人数
					</view>
				</view>
				<view class="tops">
					<view class="tops_num">
						{{eventCount}}
					</view>
					<view class="tops_rw">
						今日事件数
					</view>
				</view>
				<view class="tops">
					<view class="tops_num">
						{{taskCount}}
					</view>
					<view class="tops_rw">
						今日任务数
					</view>
				</view>
			</view>
		</view>
		<view class="body_list">
			<view class="body_list_left" @click="gengduo">
				<view class="body_list_title">
					任务接收
				</view>
				<view class="body_list_body">
					每天任务计划
				</view>
				<view class="body_list_foot">
					查看详情
					<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dfebcce0-4a4a-11eb-8ff1-d5dcf8779628.png"
					 mode="" style="width: 20px;height: 20px;vertical-align: middle;margin-left: 5px;"></image>
				</view>
			</view>
			<view class="body_list_right"  @click="tufasj">
				<view class="body_list_title">
					突发事件
				</view>
				<view class="body_list_body">
					每天突发情况
				</view>
				<view class="body_list_foot">
					查看详情
					<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/dfebcce0-4a4a-11eb-8ff1-d5dcf8779628.png"
					 mode="" style="width: 20px;height: 20px;vertical-align: middle;margin-left: 5px;"></image>
				</view>
			</view>
		</view>
		<view class="list">
			<view class="list_title">
				<view class="list_title_left">
					任务列表
				</view>
				<view class="list_title_right">
					<text @click="gengduo">查看更多></text>
				</view>
			</view>
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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				eventCount:'',
				taskCount:'0',
				taskPesCount:'0',
				arr:{},
				title: '智慧城市',
				ww: '未完成'
			}
		},
		created(){
			var that = this;
			uni.request({
				url:'http://139.9.169.87:9002/app/Event/getCurrEventCount',
				method:'GET',
				success(res){
					uni.showToast({
						title: '数据加载成功',
						icon: 'success'
					})
					that.eventCount=res.data;
					console.log(res);
				}
			});
			
			uni.request({
				url:'http://139.9.169.87:9002/app/Task/getTaskListAll',
				method:'GET',
				success(res){
					that.arr=res.data.data
				}
			})
		},
		beforeCreate(){uni.showToast({
						title: '数据加载中',
						icon: 'loading',
						duration:3000
					})},
		methods: {
			gengduo() {
			uni.navigateTo({
				url:'/components/tab_home/tab_home'
			})
			},
			tufasj(){
				uni.navigateTo({
					url:'/components/sjlist/sjlist'
				})
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
	.top {
		background-image: url('https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/764e8880-4a41-11eb-a16f-5b3e54966275.png');
		width: 100%;
		height: 115px;

		.title {
			width: 100%;
			display: flex;
			justify-content: center;
			padding-top: 50px;
			color: white;
			font-size: 20px;
			font-family: '等线';
			font-weight: bold;
		}

		.box_top {
			position: absolute;
			width: 90%;
			top: 90px;
			left: 50%;
			transform: translateX(-50%);
			height: 80px;
			background-color: white;
			border-radius: 10px;
			box-shadow: 0 0 2px #b9b9b9;
			display: flex;
			flex-direction: row;

			.tops {
				flex: 1;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-direction: column;

				.tops_num {
					font-size: 22px;
					color: #ff9126;
				}

				.tops_rw {
					font-size: 12px;
				}
			}
		}
	}

	.body_list {
		width: 90%;
		margin: 70px auto 0;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;

		.body_list_left {
			background-image: url('https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/e14067c0-4a47-11eb-bdc1-8bd33eb6adaa.png');
			background-size: 100%;
			background-repeat: no-repeat;
			width: 48%;
			height: 95px;

		}

		.body_list_right {
			background-image: url('https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/e20a6e80-4a47-11eb-bdc1-8bd33eb6adaa.png');
			background-repeat: no-repeat;
			background-size: 100%;
			width: 48%;
			height: 95px;
		}
	}

	.body_list_title {
		font-size: 18px;
		color: white;
		font-family: '等线';
		font-weight: bold;
		padding: 10px 10px 4px;

	}

	.body_list_body {
		padding: 3px 10px 4px;
		font-size: 14px;
		color: rgba($color: #ffffff, $alpha: .7);
		font-family: '等线';
		font-weight: bold;
	}

	.body_list_foot {
		padding: 10px 10px 4px;
		font-size: 12px;
		color: white;
		font-family: '等线';
		font-weight: bold;
	}

	.list {
		width: 90%;
		margin: 30px auto 0;

		.list_title {
			display: flex;
			flex-direction: row;

			.list_title_left {
				flex: 1;
				font-size: 20px;
				font-family: '等线';
				font-weight: bold;
				display: flex;
				justify-content: flex-start;
			}

			.list_title_right {
				flex: 1;
				font-family: '等线';
				font-weight: bold;
				font-size: 14px;
				color: #9e9e9e;
				display: flex;
				justify-content: flex-end;
				align-items: center;
			}
		}

		.list_box {
			width: 100%;
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
	}
</style>
