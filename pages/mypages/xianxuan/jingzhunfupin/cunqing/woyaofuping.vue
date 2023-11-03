<template>
	<view>
		<!-- 包括：标题、方案简介、扶贫方案内容，点击“确定”按钮可提交申请 -->
		<u-field label="标题" v-model="title"></u-field>
		<u-field label="方案简介" type="textarea" v-model="content"></u-field>
		<u-field label="扶贫方案内容" v-model="details" type="textarea" style="height: 300rpx;"></u-field>
		<u-button type="success" @click="tijiao">确定</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				content:'',
				details:''
			}
		},
		methods: {
			tijiao(){
				this.$u.toast('提交申请成功')
				this.title=''
				this.content=''
				this.details=''
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			},
		}
	}
</script>

<style scoped>

</style>
