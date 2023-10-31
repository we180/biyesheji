<template>
	<view>
		<!-- 车场总车位数、问题描述、纠错照片（上传一张）、提交按钮，点击提交按钮信息提交成功。 -->
		<view class="input">
			<u-field label="车场总车位数"></u-field>
			<u-field label="停车场名称"></u-field>
			<u-field label="问题描述"></u-field>
			<u-upload :action="action"></u-upload>
			<u-button type="success" @click="submit">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action:'http://192.168.1.105:10001/prod-api/common/upload'
			}
		},
		methods: {
			submit(){
				this.$u.toast('提交成功')
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
