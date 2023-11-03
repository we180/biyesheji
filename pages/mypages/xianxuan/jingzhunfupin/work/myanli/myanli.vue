<template>
	<view>
		<!-- 输入案例名称、方案内容，上传案例配图。点击“发布”按钮可发布案例。 -->
		<view class="input">
			<u-field label="案例名称" v-model="title"></u-field>
			<u-field label="方案内容" v-model="content" type="textarea" style="height: 200rpx;"></u-field>
			<u-gap></u-gap>
			<h3 style="margin-left: 16rpx;">上传案例配图</h3>
			<u-upload :action="action" ></u-upload> 
			<u-gap></u-gap>
			<u-button type="success" @click="fabu">发布</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action:"http://192.168.23.91:10001/prod-api/upload/common",
				title:'',
				content:''
			}
		},
		methods: {
			fabu(){
				this.$u.toast('发布成功!')
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
