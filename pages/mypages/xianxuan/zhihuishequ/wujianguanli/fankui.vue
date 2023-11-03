<template>
	<view>
		<u-field label="姓名" v-model="name"></u-field>
		<u-field label="电话" v-model="phone"></u-field>
		<u-field label="标题" v-model="title"></u-field>
		<u-field label="详细内容" v-model="content" type="textarea" style="height: 200rpx;"></u-field>
		<view class="photo u-m-20">
			<h3>上传图片</h3>
			<u-upload :action="action"></u-upload>
		</view>
		<u-gap></u-gap>
		<view class="">
			<u-button type="success" @click="tofankui_de">提交反馈</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'',
				phone:'',
				title:'',
				content:'',
				action:'http://192.168.23.91:10001/prod-api/common/upload'
			}
		},
		methods: {
			tofankui_de(){
				uni.navigateTo({
					url:'fankui_de'
				})
			},
		}
	}
</script>

<style>

</style>
