<template>
	<view>
		<view class="input">
			<u-field label="姓名" v-model="name"></u-field>
			<u-field label="电话" v-model="phone"></u-field>
			<u-field label="地址" v-model="address"></u-field>
			<view class="u-m-20">
				上传图片
				<view class="">
					<u-upload :action="action"></u-upload>
				</view>
			</view>
			<view class="u-m-20">
				详细内容
				<u-input type="textarea" border="border"></u-input>
			</view>
			<u-button type="success" @click="tijiao">提交</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'',
				phone:'',
				address:'',
				action:"http://192.168.23.91:10001/prod-api/common/upload"
			}
		},
		methods: {
			tijiao(){
				uni.navigateTo({
					url:'tijiao'
				})
			},
		}
	}
</script>

<style>

</style>
