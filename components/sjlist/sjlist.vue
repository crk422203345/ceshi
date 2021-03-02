<template>
	<view class="content">
		<aloys-tab :tabs="tabs" @change="onTabChange">
			<view slot="content0">
				<view class="list">
					<view class="list-item" v-for="(item,index) in arr" :key="index" @click="tz(item.id)">
						<view class="top">
							<view class="left">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/f7b20440-4a75-11eb-b997-9918a5dda011.png"
								 mode="" style="vertical-align:middle;width: 24px;height: 24px;border-radius: 50%;"></image>
								<text style="margin-left: 5px;">内容:{{item.qualityContent}}</text>
							</view>
							<view class="right">
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '0'">待派发</text>
								<text style="margin-left: 10px;color: rgb(64,179,233);" v-if="item.eventStatus === '1'">处理中</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '2'">已处理</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '3'">已结案</text>
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '4'">驳回</text>
							</view>
						</view>
						<view class="line">

						</view>
						<view class="bottom">
							<view class="left">
								<text style="color: red;color:#828282">上报人:</text>{{item.reportPerson}}
							</view>
							<view class="right">
								{{item.reportTime}}
							</view>
						</view>
					</view>
				</view>
			</view>
			<view slot="content1">
				<view class="list">
					<view class="list-item" v-for="(item,index) in arr" :key="index" @click="tz(item.id)">
						<view class="top">
							<view class="left">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/f7b20440-4a75-11eb-b997-9918a5dda011.png"
								 mode="" style="vertical-align:middle;width: 24px;height: 24px;border-radius: 50%;"></image>
								<text style="margin-left: 5px;">内容:{{item.qualityContent}}</text>
							</view>
							<view class="right">
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '0'">待派发</text>
								<text style="margin-left: 10px;color: rgb(64,179,233);" v-if="item.eventStatus === '1'">处理中</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '2'">已处理</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '3'">已结案</text>
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '4'">驳回</text>
							</view>
						</view>
						<view class="line">

						</view>
						<view class="bottom">
							<view class="left">
								<text style="color: red;color:#828282">上报人:</text>{{item.reportPerson}}
							</view>
							<view class="right">
								{{item.reportTime}}
							</view>
						</view>
					</view>
				</view>
			</view>
			<view slot="content2">
				<view class="list">
					<view class="list-item" v-for="(item,index) in arr" :key="index" @click="tz(item.id)">
						<view class="top">
							<view class="left">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/f7b20440-4a75-11eb-b997-9918a5dda011.png"
								 mode="" style="vertical-align:middle;width: 24px;height: 24px;border-radius: 50%;"></image>
								<text style="margin-left: 5px;">内容:{{item.qualityContent}}</text>
							</view>
							<view class="right">
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '0'">待派发</text>
								<text style="margin-left: 10px;color:rgb(64,179,233);" v-if="item.eventStatus === '1'">处理中</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '2'">已处理</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '3'">已结案</text>
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '4'">驳回</text>
							</view>
						</view>
						<view class="line">

						</view>
						<view class="bottom">
							<view class="left">
								<text style="color: red;color:#828282">上报人:</text>{{item.reportPerson}}
							</view>
							<view class="right">
								{{item.reportTime}}
							</view>
						</view>
					</view>
				</view>
			</view>
			<view slot="content3">
				<view class="list">
					<view class="list-item" v-for="(item,index) in arr" :key="index" @click="tz(item.id)">
						<view class="top">
							<view class="left">
								<image src="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-aliyun-zmviznaingjx656d62/f7b20440-4a75-11eb-b997-9918a5dda011.png"
								 mode="" style="vertical-align:middle;width: 24px;height: 24px;border-radius: 50%;"></image>
								<text style="margin-left: 5px;">内容:{{item.qualityContent}}</text>
							</view>
							<view class="right">
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '0'">待派发</text>
								<text style="margin-left: 10px;color:rgb(64,179,233);" v-if="item.eventStatus === '1'">处理中</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '2'">已处理</text>
								<text style="margin-left: 10px;color: black;" v-if="item.eventStatus === '3'">已结案</text>
								<text style="margin-left: 10px;color: red;" v-if="item.eventStatus === '4'">驳回</text>
							</view>
						</view>
						<view class="line">

						</view>
						<view class="bottom">
							<view class="left">
								<text style="color: red;color:#828282">上报人:</text>{{item.reportPerson}}
							</view>
							<view class="right">
								{{item.reportTime}}
							</view>
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
				nr: '道路上垃圾没及时清理',
				pf: '待派发',
				name: 'Miss Zhou',
				time: '2020.09.03'
			}
		},
		onLoad() {
			var that = this;
			
			uni.request({
				url: 'http://139.9.169.87:9002/app/Event/getEventListAll',
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
					url: "/components/sjxq/sjxq?id=" + id
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

	.list {
		margin: 0 auto;
		width: 90%;
		display: flex;
		flex-direction: column;

		.list-item {
			border-radius: 10px;
			margin: 10px auto;
			background-color: #f6f7f9;
			width: 96%;
			padding: 10px 2%;

			.top {
				display: flex;
				flex-direction: row;

				.left {
					flex: 2;
					font-size: 14px;
					display: flex;
					align-items: center;
					justify-content: flex-start;
				}

				.right {
					flex: 1;
					font-size: 14px;
					display: flex;
					align-items: center;
					justify-content: flex-end;
				}
			}

			.line {
				width: 100%;
				margin: 10px auto;
				height: 1px;
				background: #cfcfcf;
			}

			.bottom {
				display: flex;
				flex-direction: row;

				.left {
					flex: 1;
					font-size: 14px;
					display: flex;
					align-items: center;
					justify-content: flex-start;
				}

				.right {
					flex: 1;
					font-size: 14px;
					display: flex;
					align-items: center;
					justify-content: flex-end;
					color: #828282
				}
			}
		}

	}
</style>
