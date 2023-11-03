<template>
	<view>

		<view class="submit">
			<u-field label="姓名" v-model="name"></u-field>
			<u-field label="手机号" v-model="phone"></u-field>
			<u-gap></u-gap>
			<view class="u-m-20">
				上传图片
			</view>
			<view class="">
				<u-upload :action="action"></u-upload>
			</view>
			<view class="u-m-20">
				详细内容
				<u-input type="textarea" border="border" v-model="content"></u-input>
			</view>
			<view class="">
				<u-button type="success" @click="tijiao">提交</u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action: "http://192.168.23.91:10001/prod-api/common/upload",
				name: '',
				phone: '',
				content: ''
			}
		},
		methods: {
			tijiao() {
				let temp = this.adviselist
				console.log(temp);
				temp.push({
					name: this.name,
					phone: this.phone,
					content: this.content
				})
				this.$u.vuex("adviselist", temp)
				this.$u.toast('提交成功')
				setTimeout(()=>{
					uni.navigateBack({
						delta:1
					})
				},700)
			}
		}
	}
</script>

<style>

</style>
