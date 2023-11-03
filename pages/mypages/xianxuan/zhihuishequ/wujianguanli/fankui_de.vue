<template>
	<view>
		<view class="info" style="text-align: center;">
			<u-icon name="checkmark-circle-fill" label="提交成功" label-pos="bottom" size="100" label-size="40" color="#2979ff"></u-icon>
		</view>
		<u-gap></u-gap>
		<u-button type="success" @click="back">返回首页</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			back(){
				uni.redirectTo({
					url:'../zhihuishequ'
				})
			},
		}
	}
</script>

<style>

</style>
