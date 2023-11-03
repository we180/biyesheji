<template>
	<view>
		<u-field label="姓名" v-model="name"></u-field>
		<u-field label="手机号" v-model="phone"></u-field>
		<u-gap></u-gap>
		<view class="u-m-10">
			上传图片
		</view>
		<view class="">
			<u-upload :action="action"></u-upload>
		</view>
		<view class="">
			<u-button type="success" @click="baoming">报名</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action:"http://192.168.23.91:10001/prod-api/common/upload",
				name:'',
				phone:''
			}
		},
		methods: {
			baoming(){
				uni.navigateTo({
					url:'baoming_finish'
				})
			},
		}
	}
</script>

<style>

</style>
