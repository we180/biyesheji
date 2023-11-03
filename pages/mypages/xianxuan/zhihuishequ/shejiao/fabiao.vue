<template>
	<view>
		<u-field label="昵称" v-model="name"></u-field>
		<u-field label="地址" v-model="address"></u-field>
		<u-field label="标题" v-model="title"></u-field>
		<view class="upimg" style="margin: 22rpx;">
			<h3>上传图片</h3>
			<u-upload :action="action"></u-upload>
		</view>
		<view class="index" style="margin: 22rpx;">
			<h3>详细内容</h3>
			<u-input type="textarea" v-model="content" border="border"></u-input>
			<u-gap></u-gap>
			<u-button type="success" @click="back">发表</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action:'http://192.168.23.91:10001/prod-api/upload/common',
				name:'',
				address:'',
				title:'',
				content:''
			}
		},
		methods: {
			back(){
				this.$u.toast('发表成功')
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
