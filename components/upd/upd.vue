<template>
	<view>
		<view class="col">
			<uni-forms :value="formData" ref="form" labelAlign="right" labelWidth=90>
				<uni-forms-item label="质量内容:" name="name">
					<xfl-select :list="list" :clearable="false" :showItemNum="5" :placeholder="'请选择'" @change='newlist'>
					</xfl-select>
				</uni-forms-item>
				<uni-forms-item label="事件位置:" name="weizhi">
					<uni-easyinput v-model="formData.weizhi"></uni-easyinput>
				</uni-forms-item>
				<uni-forms-item label="事件部件:" name="list">
					<xfl-select :list="lists" :clearable="false" :showItemNum="5" :placeholder="'请选择'" @change='newlists'>
					</xfl-select>
				</uni-forms-item>
				<uni-forms-item label="事件详细描述:" name="miaoshu">
					<uni-easyinput v-model="formData.age" type="textarea" :autoHeight="true"></uni-easyinput>
				</uni-forms-item>
				<uni-forms-item label="图片上传:" name="updata">
					<robby-image-upload :value="imageData" v-model="formData.updata"></robby-image-upload>
				</uni-forms-item>
				<button @click="submitForm">提交</button>
			</uni-forms>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				imageData: [],
				list: [ //要展示的数据
					'道路上有垃圾',
					'垃圾桶清理不及时',
					'垃圾桶倒了',
					'园林设计不合理',
					'清洁',
					'垃圾运输',
				],
				lists: [ //要展示的数据
					'岳阳大道西',
					'深南大道东',
					'南湖大道东',
					'垃圾桶',
					'湖南理工南院',
					'道路清理',
					'云溪区',
				],
				formData: {
					name: '',
					weizhi: '',
					list:'',
					miaoshu:'',
					updata:''
				},

			}
		},
		methods: {
			submitForm(form) {
				// 手动提交表单
				this.$refs.form.submit().then((res) => {
					console.log('表单返回得值：', res)
					
				})
			},
			newlist(e){
				this.formData.name=e.newVal;
			},
			newlists(e){
				this.formData.list=e.newVal;
			}
		}
	}
</script>

<style lang="scss" scoped>
	.col {
		width: 95%;
		margin: 10px auto 0;
	}

	/deep/.uni-forms {
		min-height: 500px;
	}

	/deep/.uni-easyinput {
		margin-left: 10px;
		width: 95%;

	}

	/deep/.show-box {
		height: 35px !important;
		width: 70% !important;
		margin-left: 10px;
	}

	/deep/.imageUploadContainer  {
		margin-top: -10px!important;
	}

	button {
		border-radius: 20px !important;
		border: none !important;
		width: 50%;
		font-weight: bold;
		background: linear-gradient(to right,rgb(57,217,164),rgb(42,198,208)) !important;
		color: white !important;
	}
</style>
