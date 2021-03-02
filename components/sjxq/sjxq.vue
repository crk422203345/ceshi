<template>
	<view>
		<view class="box">
			<view class="title">

				<view class="left">
					<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/f7b20440-4a75-11eb-b997-9918a5dda011.png"
					 mode="" style="vertical-align:middle;width: 24px;height: 24px;border-radius: 50%;"></image>
					<text style="margin-left: 5px;">内容:{{obj.qualityContent}}</text>
				</view>
				<view class="right">
					<text style="margin-left: 10px;color: red;" v-if="obj.eventStatus === '0'">待派发</text>
					<text style="margin-left: 10px;color: rgb(64,179,233);" v-if="obj.eventStatus === '1'">处理中</text>
					<text style="margin-left: 10px;color: black;" v-if="obj.eventStatus === '2'">已处理</text>
					<text style="margin-left: 10px;color: black;" v-if="obj.eventStatus === '3'">已结案</text>
					<text style="margin-left: 10px;color: red;" v-if="obj.eventStatus === '4'">驳回</text>
				</view>

			</view>
			<view class="line"></view>
			<view class="body">
				<view class="list-item"><text>事件内容：</text>{{obj.eventDesc}}</view>
				<view class="list-item"><text>当前状态：</text>{{obj.handlerDesc}}</view>
				<view class="list-item"><text>上报位置：</text>{{obj.reportingLocation}}</view>
				<view class="list-item"><text>部件：</text>{{obj.partsName}}</view>
				<view class="list-item"><text>负责人：</text>{{obj.handlerPerson}}</view>
				<view class="list-item"><text>上报人：</text>{{obj.reportPerson}}</view>
				<view class="list-item"><text>上报时间：</text>{{obj.reportTime}}</view>
				<view class="list-item"><text>派发类型：</text><span v-if="obj.distributeType==='0'">自动派发</span>
					<span v-if="obj.distributeType==='1'">手动派发</span></view>
			</view>
		</view>
		<view class="imgs">
			<view class="">
				<text>事件照片:</text>
				<view class="y">
					<img :src="imgsrc" mode="widthFix" style="width: 100px"/>
				</view>
			</view>
			<view class="b">
				<text>已处理照片:</text>
				<view class="">
					<img :src="imgsrchandler" mode="widthFix" style="width: 100px"/>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				obj: {},
				imgsrc: '',
				imgsrcid: '',
				imgsrchandler: '',
				imgsrcsuffix: '&width=100&height=100',
				name: '洗扫'
			}
		},
		onLoad(e) {
			var that = this;
			uni.request({
				url: 'http://139.9.169.87:9002/app/Event/getEventById?id=' + e.id,
				method: 'GET',
				success(res) {
					uni.showToast({
						title: '数据加载成功',
						icon: 'success',
						duration: 500
					})
					that.obj = res.data.data;
					console.log(res);
					if (that.obj.eventStatus == '1') {
						that.obj.handlerDesc = '暂未处理',
							that.obj.handlerPerson = '暂无负责人'
					}
					that.imgsrcid = res.data.data.id;
					that.imgsrc = 'http://139.9.169.87:9002/app/Event/getPhoto?id=' + that.imgsrcid + that.imgsrcsuffix;
					that.imgsrchandler = 'http://139.9.169.87:9002/app/Event/getHandlerPhoto?id=' + that.imgsrcid + that.imgsrcsuffix;
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
	.imgs{
		width: 84%;
		padding: 10px 3%;
		min-height: 200px;
		margin: 20px auto 0;
		font-family: '等线';
		font-weight: bold;
		.y{margin: 10px 0;}.b{margin: 10px 0;}
		image{
			margin-top: 10px;
		}
	}
	.box {
		width: 84%;
		padding: 10px 3%;
		min-height: 200px;
		margin: 20px auto 0;
		box-shadow: 0 0 2px #e1e1e1;

		.top {
			display: flex;
			flex-direction: row;
		}

		.title {
			display: flex;
			flex-direction: row;

			.left {
				flex: 2;
				display: flex;
				font-weight: bold;
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
